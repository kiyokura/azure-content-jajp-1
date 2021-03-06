<properties
	pageTitle="Azure Active Directory ドメイン サービス プレビュー: 管理対象ドメインを管理する | Microsoft Azure"
	description="Azure Active Directory ドメイン サービスで管理されているドメインを管理する"
	services="active-directory-ds"
	documentationCenter=""
	authors="mahesh-unnikrishnan"
	manager="stevenpo"
	editor="curtand"/>

<tags
	ms.service="active-directory-ds"
	ms.workload="identity"
	ms.tgt_pltfrm="na"
	ms.devlang="na"
	ms.topic="article"
	ms.date="04/28/2016"
	ms.author="maheshu"/>

# Azure Active Directory ドメイン サービスで管理されているドメインを管理する
この記事では、Azure Active Directory (AD) ドメイン サービスで管理されているドメインを管理する方法について説明します。


## 開始する前に
この記事に記載されているタスクを実行するには、次が必要です。

1. 有効な **Azure サブスクリプション**。

2. オンプレミス ディレクトリまたはクラウド専用ディレクトリのいずれかと同期されている **Azure AD ディレクトリ**。

3. **Azure AD ドメイン サービス**が Azure AD ディレクトリに対して有効である必要があります。有効になっていない場合は、[作業の開始に関するガイド](./active-directory-ds-getting-started.md)に記載されているすべてのタスクを実行してください。

4. Azure AD ドメイン サービスで管理されたドメインの管理に使用する**ドメインに参加している仮想マシン**。そのような仮想マシンがない場合は、「[Windows Server 仮想マシンの管理対象ドメインへの参加](./active-directory-ds-admin-guide-join-windows-vm.md)」で概要が示されているすべてのタスクに従います。

5. 管理対象ドメインを管理するには、ディレクトリの **"AAD DC Administrators" グループに属するユーザー アカウント**の資格情報が必要です。

<br>


## 管理対象ドメインで実行できる管理タスク
最初に、管理対象ドメインで実行できる管理タスクを見てみましょう。"AAD DC Administrators" グループのメンバーには、管理対象ドメインで以下のようなタスクを実行できる権限が付与されます。

- コンピューターを管理対象ドメインに参加させる。

- 管理対象ドメイン内の 'AADDC Computers' と 'AADDC Users' のコンテナーに対して組み込みの GPO を構成する。

- 管理対象ドメイン上で DNS を管理する。

- 管理対象ドメイン上でカスタム組織単位 (OU) を作成し、管理する。

- 管理対象ドメインに参加しているコンピューターへの管理アクセスを取得する。


## 管理対象ドメインに対して付与されていない管理者特権
ドメインは、修正プログラムの適用、監視、バックアップの実行などのアクティビティを含め、Microsoft によって管理されます。そのため、ドメインはロックされており、ユーザーには特定の管理タスクをドメインで実行する権限がありません。例として、以下のようなタスクを実行できません。

- 管理対象ドメインのドメイン管理者特権またはエンタープライズ管理者権限は付与されません。

- 管理対象ドメインのスキーマを拡張することはできません。

- リモート デスクトップを使用して管理対象ドメインのドメイン コントローラーに接続することはできません。

- 管理対象ドメインにドメイン コントローラーを追加することはできません。


## タスク 1 - ドメインに参加している Windows Server 仮想マシンをプロビジョニングして、管理対象ドメインをリモートで管理する
Azure AD ドメイン サービスの管理対象ドメインは、Active Directory 管理センター (ADAC) や AD PowerShell などの使い慣れた Active Directory 管理ツールで管理することができます。テナント管理者には、管理対象ドメイン上のドメイン コントローラーにリモート デスクトップで接続する権限はありません。そのため、"AAD DC Administrators" グループのメンバーは、管理対象ドメインに参加している Windows Server とクライアント コンピューターから、AD 管理ツールを使用して、リモートで管理対象ドメインを管理できます。AD 管理ツールは、管理対象ドメインに参加している Windows Server とクライアント コンピューターで、リモート サーバー管理ツール (RSAT) のオプション機能の一部としてインストールできます。

最初の手順では、管理対象ドメインに参加している Windows Server 仮想マシンを設定します。手順については、「[Windows Server 仮想マシンの管理対象ドメインへの参加](active-directory-ds-admin-guide-join-windows-vm.md)」を参照してください。

### クライアント コンピューター （Windows 10 など)から管理対象ドメインをリモートで管理する
この記事の手順では、Azure AD ドメイン サービスの管理対象ドメインを管理するために、Windows Server 仮想マシンを使用することに注意してください。ただし、Windows クライアント (Windows 10 など) の仮想マシンを使用することもできます。

TechNet の 手順に従って、Windows クライアントの仮想マシンで[リモート サーバー管理ツール (RSAT) をインストール](http://social.technet.microsoft.com/wiki/contents/articles/2202.remote-server-administration-tools-rsat-for-windows-client-and-windows-server-dsforum2wiki.aspx)できます。


## タスク 2 - 仮想マシンに Active Directory 管理ツールをインストールする
ドメインに参加している仮想マシンに Active Directory 管理ツールをインストールするには、次の手順を実行します。[リモート サーバー管理ツールのインストールおよび使用](https://technet.microsoft.com/library/hh831501.aspx)の詳細については、TechNet を参照してください。

1. Azure クラシック ポータルの **[Virtual Machines]** ノードに移動します。作成した仮想マシンを選択し、ウィンドウ下部にあるコマンド バーで **[接続]** をクリックします。

    ![Windows 仮想マシンに接続する](./media/active-directory-domain-services-admin-guide/connect-windows-vm.png)

2. クラシック ポータルでは、仮想マシンへの接続に使用される .rdp ファイルを開くか保存するように求められます。ダウンロードが完了したら、.rdp ファイルをクリックします。

3. ログイン プロンプトで、'AAD DC Administrators' グループに属しているユーザーの資格情報を使用します。この例では " bob@domainservicespreview.onmicrosoft.com" です。

4. スタート画面で、**[サーバー マネージャー]** を開きます。[サーバー マネージャー] ウィンドウの中央ペインで **[役割と機能の追加]** をクリックします。

    ![仮想マシンでのサーバー マネージャーの起動](./media/active-directory-domain-services-admin-guide/install-rsat-server-manager.png)

5. **[役割と機能の追加]** ウィザードの **[開始する前に]** ページで **[次へ]** をクリックします。

    ![ページを開始する前に](./media/active-directory-domain-services-admin-guide/install-rsat-server-manager-add-roles-begin.png)

6. **[インストールの種類]** ページで、**[役割ベースまたは機能ベースのインストール]** オプションが選択された状態にして **[次へ]** をクリックします。

	![インストールの種類のページ](./media/active-directory-domain-services-admin-guide/install-rsat-server-manager-add-roles-type.png)

7. **[サーバーの選択]** ページで、サーバー プールから現在の仮想マシンを選択して **[次へ]** をクリックします。

	![サーバー選択ページ](./media/active-directory-domain-services-admin-guide/install-rsat-server-manager-add-roles-server.png)

8. **[サーバーの役割]** ページで、**[次へ]** をクリックします。サーバーに役割をインストールしないため、このページはスキップします。

9. **[機能]** ページで、**[リモート サーバー管理ツール]** ノードをクリックして展開し、次に **[役割管理ツール]** ノードをクリックして展開します。役割管理ツールの一覧から、次のように **[AD DS および AD LDS ツール]** 機能を選択します。

	![機能ページ](./media/active-directory-domain-services-admin-guide/install-rsat-server-manager-add-roles-ad-tools.png)

10. **[確認]** ページで、**[インストール]** をクリックして仮想マシンに AD および AD LDS ツールの機能をインストールします。機能のインストールが正常に完了したら、**[閉じる]** をクリックして **[役割と機能の追加]** ウィザードを終了します。

	![確認ページ](./media/active-directory-domain-services-admin-guide/install-rsat-server-manager-add-roles-confirmation.png)


## タスク 3 - 管理対象ドメインへの接続と確認
ドメインに参加している仮想マシンに AD 管理ツールがインストールされたら、その管理ツールを使って管理対象ドメインを確認し、管理することができます。

> [AZURE.NOTE] 管理対象ドメインを管理するには、"AAD DC Administrators" グループのメンバーである必要があります。

1. スタート画面で、**[管理ツール]** をクリックします。仮想マシンにインストールされた AD 管理ツールを確認できます。

	![サーバーにインストールされている管理ツール](./media/active-directory-domain-services-admin-guide/install-rsat-admin-tools-installed.png)

2. **[Active Directory 管理センター]** をクリックします。

	![Active Directory 管理センター](./media/active-directory-domain-services-admin-guide/adac-overview.png)

3. 左ウィンドウのドメイン名 ('contoso100.com' など) をクリックしてドメインを確認します。'AADDC Computers' と 'AADDC Users' という名前の 2 つのコンテナーがあります。

    ![ADAC: ドメインの表示](./media/active-directory-domain-services-admin-guide/adac-domain-view.png)

4. **'AADDC Users'** というコンテナーをクリックすると、管理対象ドメインに属しているすべてのユーザーとグループが表示されます。ユーザー アカウントと Azure AD テナントからのグループがこのコンテナー内にあります。この例では、ユーザー 'bob' のユーザー アカウントおよび 'AAD DC Administrators' という名前のグループがこのコンテナーで利用できます。

    ![ADAC: ドメイン ユーザー](./media/active-directory-domain-services-admin-guide/adac-aaddc-users.png)

5. **'AADDC Computers'** という名前のコンテナーをクリックすると、この管理対象ドメインに参加しているコンピューターが表示されます。ドメインに参加している現在の仮想マシンのエントリが表示されます。Azure AD ドメイン サービスで管理されているドメインに参加しているすべてのコンピューターのコンピューター アカウントが、この 'AADDC Computers' コンテナーに表示されます。

    ![ADAC: ドメインに参加しているコンピューター](./media/active-directory-domain-services-admin-guide/adac-aaddc-computers.png)

<br>

## 関連コンテンツ

- [Azure AD ドメイン サービス - 作業開始ガイド](./active-directory-ds-getting-started.md)

- [Azure AD ドメイン サービスで管理されているドメインに Windows Server 仮想マシンを参加させる](active-directory-ds-admin-guide-join-windows-vm.md)

- [リモート サーバー管理ツールのデプロイ](https://technet.microsoft.com/library/hh831501.aspx)

<!---HONumber=AcomDC_0518_2016-->