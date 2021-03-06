<properties
	pageTitle="Azure AD のフェデレーション互換性リスト"
	description="このページには、シングル サインオンの実装に使用できる Microsoft 以外の ID プロバイダーが記載されています。"
	services="active-directory"
	documentationCenter=""
	authors="billmath"
	manager="stevenpo"
	editor="curtand"/>

<tags
	ms.service="active-directory"
	ms.workload="identity"
	ms.tgt_pltfrm="na"
	ms.devlang="na"
	ms.topic="article"
	ms.date="05/12/2016"
	ms.author="billmath"/>

# Azure AD のフェデレーション互換性リスト
Azure Active Directory は、Microsoft 以外のソリューションを必要とすることなくハイブリッド実装とクラウド専用の実装を実現するために、Office 365 などの Microsoft オンライン サービスに対してシングル サインオンとアプリケーション アクセスのセキュリティ強化を提供します。Office 365 は、Microsoft のオンライン サービスのほとんどと同様に、ディレクトリ サービス、認証、承認のために Azure Active Directory と統合されます。また、Azure Active Directory では、多数の SaaS アプリケーションやオンプレミスの Web アプリケーションにもシングル サインオンを提供しています。サポートされている SaaS アプリケーションについては、Azure Active Directory アプリケーション ギャラリーを参照してください。

Microsoft 以外のフェデレーション ソリューションに投資している組織のために、このトピックでは、次の "Azure Active Directory フェデレーション互換性リスト" に記載されている Microsoft 以外の ID プロバイダーを使用して、Microsoft オンライン サービスを使用する Windows Server Active Directory ユーザーのシングル サインオンを構成する場合のガイダンスを示しています。

Microsoft では、次のように、Microsoft 以外の ID プロバイダーを使用して、Azure Active Directory でよく見られる一連のユース ケースに対してシングル サインオン エクスペリエンスをテストしました。

>[AZURE.IMPORTANT] Microsoft でテストしたのは、これらのシングル サインオン シナリオのフェデレーション機能のみです。これらのシングル サインオン シナリオでは、同期、2 要素認証などのコンポーネントのテストは実施していません。

>このプログラムでは、UPN への代替 ID によるサインインの使用もテストしません。



- [Azure Active Directory](#azure-active-directory)
- [Optimal IDM Virtual Identity Server Federation Services](#optimal-idm-virtual-identity-server-federation-services) 
- [PingFederate 6.11](#pingfederate-611) 
- [PingFederate 7.2](#pingfederate-72) 
- [Centrify](#centrify) 
- [IBM Tivoli Federated Identity Manager 6.2.2](#ibm-tivoli-federated-identity-manager-622) 
- [SecureAuth IdP 7.2.0](#secureauth-idp-720) 
- [CA SiteMinder 12.52](#ca-siteminder-1252) 
- [RadiantOne CFS 3.0](#radiantone-cfs-30) 
- [Okta](#okta) 
- [OneLogin](#onelogin) 
- [NetIQ Access Manager 4.0.1](#netiq-access-manager-401) 
- [BIG-IP と BIG-IP Access Policy Manager Version 11.3x ～ 11.6x](#big-ip-with-access-policy-manager-big-ip-ver-113x-116x) 
- [VMware Workspace Portal Version 2.1](#vmware-workspace-portal-version-21) 
- [Sign&go 5.3](#signampgo-53) 
- [IceWall Federation Version 3.0](#icewall-federation-version-30) 
- [CA Secure Cloud](#ca-secure-cloud) 
- [Dell One Identity Cloud Access Manager v7.1](#dell-one-identity-cloud-access-manager-v71) 
- [AuthAnvil Single Sign On 4.5](#authavil-single-sign-on-45) 

>[AZURE.IMPORTANT] これらはサード パーティ製品であるため、Microsoft では、これらの ID プロバイダーに関するデプロイ、構成、トラブルシューティング、ベスト プラクティスなどの問題や質問をサポートしていません。これらの ID プロバイダーに関するサポートと質問については、サポートしているサード パーティに直接お問い合わせください。

>これらのサード パーティの ID プロバイダーについては、WS-Federation プロトコルと WS-Trust プロトコルのみを使用して Microsoft クラウド サービスとの相互運用性のテストが済んでいます。SAML プロトコルを使用したテストは実施されていません。

## Azure Active Directory 
Azure Active Directory は、オンプレミスの Active Directory とのフェデレーションを介してユーザーを認証するか、オンプレミスのフェデレーション サーバーとのフェデレーションを介さずにパスワード同期を使用してユーザーを認証することができます。

このサインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。


| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |なし|
| Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション | サポートされています |なし|
| Outlook や ActiveSync などの電子メール リッチ クライアント | サポートされています |なし|
|Office 2016 などの ADAL を使用した最新のアプリケーション| サポートされています|なし|

AD FS を使用した Azure Active Directory の使用の詳細については、[Active Directory フェデレーション サービス (ADFS)](active-directory-aadconnect-get-started-custom.md#configuring-federation-with-ad-fs) に関するページを参照してください。

パスワード同期を使用した Azure Active Directory の使用の詳細については、[Azure AD Connect](active-directory-aadconnect.md) に関するページを参照してください。


## Optimal IDM Virtual Identity Server Federation Services 
Optimal IDM Virtual Identity Server Federation Services では、お客様のオンプレミスの Active Directory に属するユーザーを認証できます。

このシングル サインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。


| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |なし|
| Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション | サポートされています |統合 Windows 認証|
| Outlook や ActiveSync などの電子メール リッチ クライアント | サポートされています |クライアント アクセス ポリシーの詳細については、「[Limiting Access to Office 365 Services Based on the Location of the Client (クライアントの場所に基づいた Office 365 サービスへのアクセスの制限)](https://technet.microsoft.com/library/hh526961.aspx)」を参照してください|



## PingFederate 6.11 

PingFederate 6.11 は、広く使用されている WS-Federation ID 標準を実装して、シングル サインオンと属性交換フレームワークを提供しています。

このシングル サインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。


| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |なし|
| Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション | サポートされています |なし (これより前のバージョンは 6.11 にアップグレードする必要があります)|
| Outlook や ActiveSync などの電子メール リッチ クライアント | サポートされています |なし|

Active Directory ユーザーにシングル サインオン エクスペリエンスを提供するように PingFederate でこの STS を構成する手順については、[こちら](http://go.microsoft.com/fwlink/?LinkID=266321)から PDF をダウンロードしてください。

## PingFederate 7.2 
PingFederate 7.2 は、広く使用されている WS-Federation/WS-Trust ID 標準を実装して、シングル サインオンと属性交換フレームワークを提供しています。

このシングル サインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。


| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |なし|
| Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション | サポートされています |なし|
| Outlook や ActiveSync などの電子メール リッチ クライアント | サポートされています |なし|

Active Directory ユーザーにシングル サインオン エクスペリエンスを提供するように PingFederate でこの STS を構成する手順については、[こちら](http://documentation.pingidentity.com/display/PF72/PingFederate+7.2)を参照してください。

## Centrify 
Centrify では、オンプレミスのフェデレーション サーバーをホストする必要なく Office 365 のフェデレーション シングル サインオン エクスペリエンスを提供します。

このシングル サインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。


| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |なし|
| Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション | サポートされています |なし|
| Outlook や ActiveSync などの電子メール リッチ クライアント | サポートされています |クライアント アクセス制御はサポートされていません 

Centrify の詳細については、[こちら](http://www.centrify.com/cloud/apps/single-sign-on-for-office-365.asp)を参照してください。

## IBM Tivoli Federated Identity Manager 6.2.2 
IBM Security Access Manager for Microsoft Applications 1.4 を使用する IBM Tivoli Federated Identity Manager 6.2.2 は、広く使用されている WS-Federation/WS-Trust ID 標準を実装して、シングル サインオンと属性交換フレームワークを提供しています。

このシングル サインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。

| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |なし|
| Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション | サポートされています |なし|
| Outlook や ActiveSync などの電子メール リッチ クライアント | サポートされています |なし|

IBM Tivoli Federated Identity Manager の詳細については、「[IBM Security Access Manager for Microsoft Applications](http://www-01.ibm.com/support/docview.wss?uid=swg24029517)」を参照してください。

## SecureAuth IdP 7.2.0 
SecureAuth IdP 7.2.0 は、広く使用されている WS-Federation/WS-Trust ID 標準を実装して、シングル サインオン エクスペリエンスと属性交換フレームワークを提供しています。

このシングル サインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。

| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |なし|
| Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション | サポートされています |なし|
| Outlook や ActiveSync などの電子メール リッチ クライアント | サポートされています |なし|

SecureAuth の詳細については、[SecureAuth IdP](http://go.microsoft.com/?linkid=9845293) に関するページを参照してください。

## CA SiteMinder 12.52 
CA SiteMinder Federation 12.52 は、広く使用されている WS-Federation/WS-Trust ID 標準を実装して、シングル サインオンと属性交換フレームワークを提供しています。

このシングル サインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。

| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |統合 Windows 認証|
| Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション | サポートされています |統合 Windows 認証|
| Outlook や ActiveSync などの電子メール リッチ クライアント | サポートされています |なし|

CA SiteMinder の詳細については、[CA SiteMinder Federation](http://www.ca.com/us/products/ca-single-sign-on.html) に関するページを参照してください。

## RadiantOne CFS 3.0 
RadiantOne Cloud Federation Service (CFS) 3.0 は、広く使用されている WS-Federation/WS-Trust ID 標準を実装して、シングル サインオンと属性交換フレームワークを提供しています。

このシングル サインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。

| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |なし|
| Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション | サポートされています |統合 Windows 認証|
| Outlook や ActiveSync などの電子メール リッチ クライアント | サポートされています |なし|

RadiantOne CFS の詳細については、[RadiantOne CFS](http://www.radiantlogic.com/products/radiantone-cfs/) に関するページを参照してください。


## Okta 
Okta は、広く使用されている WS-Federation/WS-Trust ID 標準を実装して、シングル サインオンと属性交換フレームワークを提供しています。

このシングル サインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。


| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |統合 Windows 認証では、追加の Web サーバーと Okta アプリケーションのセットアップが必要です。|
| Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション | サポートされています |統合 Windows 認証|
| Outlook や ActiveSync などの電子メール リッチ クライアント | サポートされています |なし|

Okta の詳細については、[Okta](https://www.okta.com/) Web サイトを参照してください。
 
## OneLogin 
2014 年 5 月にテストされた OneLogin は、広く使用されている WS-Federation/WS-Trust ID 標準を実装して、シングル サインオンと属性交換フレームワークを提供しています。

このシングル サインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。

| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |統合 Windows 認証|
| Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション | サポートされています |統合 Windows 認証|
| Outlook や ActiveSync などの電子メール リッチ クライアント | サポートされています |なし|

OneLogin の詳細については、[OneLogin](https://www.onelogin.com/) Web サイトを参照してください。

## NetIQ Access Manager 4.0.1 
NetIQ Access Manager 4.0.1 は、広く使用されている WS-Federation/WS-Trust ID 標準を実装して、シングル サインオンと属性交換フレームワークを提供しています。

このシングル サインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。

| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |**Kerberos Contract がサポートされています|
|Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション|サポートされています|統合 Windows 認証はサポートされていません|
|Outlook や ActiveSync などの電子メール リッチ クライアント|サポートされています|なし|

**NetIQ は、Kerberos Contract の構成を介した Kerberos 認証をサポートしています。この構成に関するサポートについては、NetIQ 社に問い合わせるか、セットアップ ガイドを参照してください。NetIQ Access Manager の詳細については、[NetIQ Access Manager](https://www.netiq.com/documentation/netiqaccessmanager4/identityserverhelp/data/b12iqp0m.html) に関するページを参照してください。

## BIG-IP と BIG-IP Access Policy Manager Version 11.3x ～ 11.6x 
BIG-IP with Access Policy Manager、(APM) BIG-IP Version 11.3x ～ 11.6x は、広く使用されている SAML ID 標準を実装して、シングル サインオン エクスペリエンスと属性交換フレームワークを提供しています。

このシングル サインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。

| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |なし|
| Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション | サポートされていません |サポートされていません|
| Outlook や ActiveSync などの電子メール リッチ クライアント | サポートされています |なし|

BIG-IP Access Policy Manager の詳細については、[BIG-IP Access Policy Manager](https://f5.com/products/modules/access-policy-manager) に関するページを参照してください。

Active Directory ユーザーにシングル サインオン エクスペリエンスを提供するように BIG-IP Access Policy Manager でこの STS を構成する手順については、[こちら](http://www.f5.com/pdf/deployment-guides/microsoft-office-365-idp-dg.pdf)から PDF をダウンロードしてください。

## VMware Workspace Portal Version 2.1 
VMware Workspace Portal Version 2.1 は、広く使用されている WS-Federation/WS-Trust ID 標準を実装して、シングル サインオンと属性交換フレームワークを提供しています。

このシングル サインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。

| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |統合 Windows 認証はサポートされていません|
| Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション | サポートされています |統合 Windows 認証はサポートされていません|
| Outlook や ActiveSync などの電子メール リッチ クライアント | サポートされています |なし|

VMware Workspace Portal Version 2.1 の詳細については、[こちら](http://pubs.vmware.com/workspace-portal-21/topic/com.vmware.ICbase/PDF/workspace-portal-21-resource.pdf)から PDF をダウンロードしてください。

## Sign&go 5.3 
Sign&go 5.3 は、広く使用されている WS-Federation/WS-Trust ID 標準を実装して、シングル サインオンと属性交換フレームワークを提供しています。

このシングル サインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。

| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |Kerberos Contract がサポートされています |
| Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション | サポートされています |なし|
| Outlook や ActiveSync などの電子メール リッチ クライアント | サポートされています |なし|


Sign&go 5.3 は、Kerberos Contract の構成を介した Kerberos 認証をサポートしています。この構成に関するサポートについては、Ilex に問い合わせるか、[こちら](http://www.ilex-international.com/docs/sign&go_wsfederation_en.pdf)のセットアップ ガイドを参照してください。


## IceWall Federation Version 3.0 
IceWall Federation Version 3.0 は、広く使用されている WS-Federation/WS-Trust ID 標準を実装して、シングル サインオンと属性交換フレームワークを提供しています。

このシングル サインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。

| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |統合 Windows 認証はサポートされていません|
| Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション | サポートされています |統合 Windows 認証はサポートされていません|
| Outlook や ActiveSync などの電子メール リッチ クライアント | サポートされています |なし|

IceWall Federation の詳細については、[こちら](http://h50146.www5.hp.com/products/software/security/icewall/eng/federation/)と[こちら](http://h50146.www5.hp.com/products/software/security/icewall/federation/office365.html)を参照してください。

## CA Secure Cloud 

CA Secure Cloud は、広く使用されている WS-Federation/WS-Trust ID 標準を実装して、シングル サインオンと属性交換フレームワークを提供しています。

このシングル サインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。

| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |統合 Windows 認証はサポートされていません|
| Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション | サポートされています |統合 Windows 認証はサポートされていません|
| Outlook や ActiveSync などの電子メール リッチ クライアント | サポートされています |なし|

CA Secure Cloud の詳細については、[CA Secure Cloud](http://www.ca.com/us/products/security-as-a-service.aspx) に関するページを参照してください。

## Dell One Identity Cloud Access Manager v7.1 
Dell One Identity Cloud Access Manager は、広く使用されている WS-Federation/WS-Trust ID 標準を実装して、シングル サインオンと属性交換フレームワークを提供しています。

このシングル サインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。

| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |なし|
| Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション | サポートされています |なし|
| Outlook や ActiveSync などの電子メール リッチ クライアント | サポートされています |なし|

Dell One Identity Cloud Access Manager の詳細については、[Dell One Identity の Cloud Access Manager](http://software.dell.com/products/cloud-access-manager) に関するページを参照してください。

 Office 365 ユーザーにシングル サインオン エクスペリエンスを提供するようにこの STS を構成する手順については、[Office 365 ユーザーの構成](http://documents.software.dell.com/dell-one-identity-cloud-access-manager/7.1/how-to-configure-microsoft-office-365)に関するページを参照してください。

## AuthAnvil Single Sign On 4.5 
AuthAnvil Single Sign On 4.5 は、広く使用されている WS-Federation/WS-Trust ID 標準を実装して、シングル サインオンと属性交換フレームワークを提供しています。

このシングル サインオン エクスペリエンスのシナリオにおけるサポート状況を次に示します。

| クライアント |サポート |例外|
| --------- | --------- |--------- |
| Exchange Web Access や SharePoint Online などの Web ベースのクライアント | サポートされています |統合 Windows 認証はサポートされていません|
| Lync、Office サブスクリプション、CRM などのリッチ クライアント アプリケーション | サポートされています |統合 Windows 認証はサポートされていません|
| Outlook や ActiveSync などの電子メール リッチ クライアント | サポートされています |なし|


詳細については、[AuthAnvil のシングル サインオン](https://help.scorpionsoft.com/entries/26538603-How-can-I-Configure-Single-Sign-On-for-Office-365-)に関するページを参照してください。

<!---HONumber=AcomDC_0518_2016-->