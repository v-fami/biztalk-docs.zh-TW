---
title: BizTalk Adapter for mySAP Business Suite 的架構概觀 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture of SAP adapter
- adapters, architecture
ms.assetid: 1b45edb0-2476-427b-b6cd-41e38ed815e0
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d571cdd3beea2bc9a57ec7ad15f865e7ef51e53a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite"></a>BizTalk Adapter for mySAP Business Suite 的架構概觀
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]實作[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結，其中包含單一的自訂傳輸繫結項目，可讓與 SAP 系統的通訊。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]包裝[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]執行階段，並公開至應用程式可以透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道架構。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會與透過 SAP Unicode RFC SDK (librfc32u.dll) 的 64 位元或 32 位元版本的 SAP 系統通訊。 

下圖顯示使用開發解決方案的端對端架構[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
 ![SAP 端&#45;至&#45;結束架構](../../adapters-and-accelerators/adapter-sap/media/9ba0c31f-90df-444d-8192-42743c893d51.gif "9ba0c31f-90df-444d-8192-42743c893d51")  
  
## <a name="consuming-the-adapter"></a>使用配接器  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]公開為 SAP 系統[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務用戶端應用程式。 用戶端應用程式交換的 SOAP 訊息[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道可執行作業，而且存取 SAP 系統上的資料。 上圖顯示四種方式在其中[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可以取用。  
  
-   透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道執行 SAP 系統上的作業使用的應用程式[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型交換 SOAP 訊息直接與[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 如需有關開發方案[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型程式設計，請參閱[開發應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)。  
  
-   透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型應用程式呼叫之方法上[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]SAP 系統上執行作業的用戶端。 A[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端模型所公開的作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]做為.NET 方法。 您可以使用[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]或 svcutil.exe 工具來建立[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]所公開的中繼資料從用戶端類別[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 如需有關[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型程式設計和[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[開發應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)。  
  
-   透過 BizTalk 連接埠是設定為使用 BizTalk WCF 自訂配接器與 SAP 繫結設定的繫結中的 WCF 自訂傳輸類型為[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式。 BizTalk WCF 自訂配接器可讓通訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式和[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務。 BizTalk WCF 自訂配接器支援自訂[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]透過 WCF 自訂繫結的傳輸類型，可讓您設定任何[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]公開至組態系統當做 BizTalk Wcf-custom 配接器所使用的繫結的繫結。 如需有關如何使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案，請參閱[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)。 支援 BizTalk 交易 BizTalk 分層通道繫結項目可以載入由 SAP 繫結上設定繫結屬性。  
  
-   透過 IIS 裝載的 Web 服務。 在此案例中，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]透過公開[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務 proxy，裝載於 IIS 使用其中一種標準[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]HTTP 繫結。  
  
-   透過[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]。 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]之上執行[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]並提供給 SAP 系統的 ADO.NET 介面。  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]和 SAP RFC 程式庫一律裝載同處理序的應用程式或服務取用配接器。  
  
## <a name="sap-adapter-and-wcf"></a>SAP 配接器和 WCF  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] 提供程式設計模型，根據 SOAP 訊息交換，透過用戶端和服務之間的通道。 通訊的用戶端和服務所公開的端點之間傳送這些訊息。  
  
 端點包含*端點位址*速率接收訊息的位置指定*繫結*指定用來交換訊息，以及通訊協定*合約*指定端點所公開的作業和資料類型。 繫結堆疊在彼此的上方來定義與端點交換訊息的方式的一或多個繫結項目所組成。  
  
 最少的傳輸和編碼用來與端點交換訊息，必須指定繫結。 端點之間交換訊息會透過所組成的一個或多個通道的通道堆疊。 每個通道是其中一個繫結項目設定之端點的繫結中的具象實作。  
  
[WCF 文件](http://go.microsoft.com/fwlink/?LinkID=196850)包含更多詳細資料，關於[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，而[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]程式設計模型。  
  
 [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]公開[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]自訂繫結，SAP 繫結 (**Microsoft.Adapters.SAP.SAPBinding**)。 根據預設，此繫結包含單一的自訂傳輸繫結項目，SAP 配接器繫結項目 (**Microsoft.Adapters.SAP.SAPAdapter**)，可讓 SAP 系統上的作業。 當使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以設定**EnableBizTalkCompatibilityMode**載入自訂繫結項目，BizTalk 分層通道繫結項目，在 SAP 配接器繫結屬性繫結項目。 BizTalk 層次通道繫結項目在內部實作[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]且不會公開之外的 SAP 繫結。  
  
 **Microsoft.Adapters.SAP.SAPBinding** （SAP 繫結） 和**Microsoft.Adapters.SAP.SAPAdapter** （SAP 配接器繫結項目） 都是公用的類別，也會公開至組態系統。 因為 SAP 配接器繫結項目公開的您可以建立自己的自訂[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]能夠擴充功能的繫結[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 例如，您可以實作自訂繫結以支援企業單一登入 (SSO) 中[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道或[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型程式設計方案，來彙總資料庫作業為單一的多功能作業，或執行自訂的應用程式所實作的作業與 SAP 系統上的作業之間的結構描述轉換。  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]建置最上層的[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]並執行最上層的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]執行階段。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]軟體架構和工具，基礎結構提供[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]利用一組豐富的功能提供給使用者和配接器用戶端。  

## <a name="sap-adapter-and-the-wcf-lob-adapter-sdk"></a>SAP 配接器和 WCF LOB 配接器 SDK
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]實作運用功能所提供的核心元件的一組[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]並提供連線至 SAP 系統，透過 SAP Unicode RFC SDK 程式庫 (librfc32u.dll)。  
  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]做為透過此軟體層[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]介面[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]，而且可以當做透過此圖層的 RFC SDK[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與 SAP 系統的介面。 下圖顯示的內部元件之間的關聯性[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]之間以及這些元件與 RFC SDK。  
  
 ![內部配接器元件的關係](../../adapters-and-accelerators/adapter-sap/media/10f97b95-4e82-4592-ba07-0f58478305c2.gif "10f97b95-4e82-4592-ba07-0f58478305c2")  
  
## <a name="connection-to-the-sap-system"></a>連接至 SAP 系統  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與 SAP 系統，透過 SAP Unicode RFC SDK 程式庫 (librfc32u.dll) 連線。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援 32 位元和 64 位元版本的 SAP RFC sdk。 SAP RFC SDK 可讓外部程式的 SAP 系統上呼叫 ABAP 函式。  
  
 您連接到 SAP 系統所提供的連線 URI 以[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援下列種類的 SAP 系統的連線：  
  
-   應用程式主機型連線 (A)，在其中[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]直接連接到 SAP 應用程式伺服器。  
  
-   負載平衡連接 (B)，在其中[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]連接至 SAP 訊息伺服器。  
  
-   目的地為基礎的連接 (D)，連接至 SAP 系統由 saprfc.ini 組態檔中的目的地。 A、 B 和 R 支援連線類型。  
  
-   接聽程式連接 (R)、 Rfc、 tRFC 和透過 RFC 目的地上的 SAP 系統所指定的接聽程式的主機、 接聽程式閘道服務和接聽程式的程式識別碼，直接在 連線 URI 中或是以 R 為基礎的 Idoc，配接器的接收saprfc.ini 組態檔中的目的地。  
  
 如需 saprfc.ini 檔案的詳細資訊，請參閱 「 SAPRFC。INI 檔案 」 中的[SAP 文件集](https://help.sap.com/doc/PRODUCTION/saphelp_nwpi711/7.1.1/en-US/48/c4168eca64581de10000000a42189c/frameset.htm)。  
  
 如需有關如何[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]連接至 SAP 系統，請參閱[建立連接至 SAP 系統](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md)。  
  
## <a name="see-also"></a>另請參閱  
 [了解 BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)