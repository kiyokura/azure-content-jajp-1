<properties
	pageTitle="Azure App Service Mobile Apps で Universal Windows Platform (UWP) アプリを作成する | Microsoft Azure"
	description="このチュートリアルに従って、Azure モバイル アプリ バックエンドを使用して、C#、Visual Basic、または JavaScript で Universal Windows Platform (UWP) アプリの開発を開始します。"
	services="app-service\mobile"
	documentationCenter="windows"
	authors="ggailey777"
	manager="erikre"
	editor=""/>

<tags
	ms.service="app-service-mobile"
	ms.workload="mobile"
	ms.tgt_pltfrm="mobile-windows"
	ms.devlang="dotnet"
	ms.topic="hero-article"
	ms.date="05/03/2016"
	ms.author="glenga"/>

#Create a Windows app (Windows アプリの作成)

[AZURE.INCLUDE [app-service-mobile-selector-get-started](../../includes/app-service-mobile-selector-get-started.md)]

##概要

このチュートリアルでは、Universal Windows Platform (UWP) アプリにクラウドベースのバックエンド サービスを追加する方法を示します。詳細については、「[モバイル アプリとは](app-service-mobile-value-prop.md)」を参照してください。次に示すのは、完了したアプリの画面キャプチャです。

![Completed desktop app](./media/app-service-mobile-windows-store-dotnet-get-started/mobile-quickstart-completed-desktop.png) デスクトップで実行されています。

![Completed phone app](./media/app-service-mobile-windows-store-dotnet-get-started/mobile-quickstart-completed.png) スマート フォンで実行されています。

UWP アプリの他のすべての Mobile Apps チュートリアルを行う前に、このチュートリアルを完了する必要があります。

##前提条件

このチュートリアルを完了するには、以下が必要です。

* アクティブな Azure アカウントアカウントがない場合、Azure 試用版にサインアップして、最大 10 件の無料モバイル アプリを入手できます。このアプリは評価終了後も使用できます。詳細については、[Azure の無料試用版サイト](https://azure.microsoft.com/pricing/free-trial/)を参照してください。

* [Visual Studio Community 2015] 以降のバージョン。

>[AZURE.NOTE] Azure アカウントにサインアップする前に Azure App Service を開始する場合は、「[Azure App Service アプリケーションの作成](https://tryappservice.azure.com/?appServiceName=mobile)」にアクセスしてください。有効期間が短いスターター モバイル アプリを App Service ですぐに作成できます。このサービスの利用にあたり、クレジット カードは必要ありません。契約も必要ありません。

##新しい Azure Mobile App バックエンドの作成

新しいモバイル アプリ バックエンドを作成するには、次の手順に従います。

[AZURE.INCLUDE [app-service-mobile-dotnet-backend-create-new-service](../../includes/app-service-mobile-dotnet-backend-create-new-service.md)]

これで、モバイル クライアント アプリケーションで使用できる Azure モバイル アプリ バックエンドのプロビジョニングが完了しました。次は、簡単な "todo list" バックエンドのサーバー プロジェクトをダウンロードして、それを Azure に発行します。

## サーバー プロジェクトの構成

[AZURE.INCLUDE [app-service-mobile-configure-new-backend.md](../../includes/app-service-mobile-configure-new-backend.md)]

##クライアント プロジェクトのダウンロードおよび実行

モバイル アプリ バックエンドを構成した後は、新しいクライアント アプリを作成したり、既存のアプリを Azure に接続するように変更したりできます。このセクションでは、モバイル アプリ バックエンドに接続するようにカスタマイズされた UWP アプリ テンプレート プロジェクトをダウンロードします。

1. モバイル アプリ バックエンドの **[クイック スタート]** ブレードに戻り、**[新しいアプリの作成]**、**[ダウンロード]** の順にクリックして、圧縮されたプロジェクト ファイルをローカル コンピューターに展開します。

	![Download Windows quickstart project](./media/app-service-mobile-windows-store-dotnet-get-started/mobile-app-windows-quickstart.png)

3. (省略可能) サーバー プロジェクトと同じソリューションに UWP アプリ プロジェクトを追加します。これにより、必要であれば、同じ Visual Studio ソリューションでアプリとバックエンドの両方をより簡単にデバッグおよびテストできるようになります。UWP アプリ プロジェクトをソリューションに追加するには、Visual Studio 2015 以降のバージョンを使用している必要があります。

4. UWP アプリをスタートアップ プロジェクトにして F5 キーを押し、アプリをデプロイおよび実行します。

5. アプリで、**[Insert a TodoItem]** テキスト ボックスに意味のあるテキスト (たとえば、「 *チュートリアルの完了* 」) を入力し、**[Save]** をクリックします。

	![Windows quickstart complete desktop](./media/app-service-mobile-windows-store-dotnet-get-started/mobile-quickstart-startup.png)

	これで、Azure でホストされている新しいモバイル アプリ バックエンドに POST 要求が送信されます。

6. (省略可能) アプリを停止し、別のデバイスまたはモバイル エミュレーターで再開します。

	![Windows quickstart complete phone](./media/app-service-mobile-windows-store-dotnet-get-started/mobile-quickstart-completed.png)

	UWP アプリの開始後、前の手順で保存したデータが Azure から読み込まれる点に注目してください。

##次のステップ

* [アプリに認証を追加する](app-service-mobile-windows-store-dotnet-get-started-users.md) ID プロバイダーを使用してアプリのユーザーを認証する方法について説明します。

* [アプリにプッシュ通知を追加する](app-service-mobile-windows-store-dotnet-get-started-push.md) アプリにプッシュ通知のサポートを追加して、Azure Notification Hubs を使用してプッシュ通知を送信するようにモバイル アプリ バックエンドを構成する方法について説明します。

* [アプリのオフライン同期を有効にする](app-service-mobile-windows-store-dotnet-get-started-offline-data.md) Mobile App バックエンドを使用して、オフライン サポートをアプリに追加する方法について説明します。オフライン同期を使用すると、エンド ユーザーはネットワークにアクセスできなくても、データの表示、追加、変更など、モバイル アプリとやり取りできます。

<!-- Anchors. -->
<!-- Images. -->
<!-- URLs. -->
[Mobile App SDK]: http://go.microsoft.com/fwlink/?LinkId=257545
[Azure portal]: https://portal.azure.com/
[Visual Studio Community 2015]: https://go.microsoft.com/fwLink/p/?LinkID=534203

<!---HONumber=AcomDC_0629_2016-->