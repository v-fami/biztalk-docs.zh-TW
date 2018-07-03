---
title: BizTalk Adapter for mySAP Business Suite 的架構概觀 |Microsoft Docs
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
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6e05cde05819edf1bbe1525d87797bf1131f1d5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006047"
---
# <a name="architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite"></a>BizTalk Adapter for mySAP Business Suite 的架構概觀
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]實作[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結，其中包含可啟用與 SAP 系統通訊的單一自訂傳輸繫結項目。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]包裝[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]執行階段和應用程式可以透過公開[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道架構。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會透過 SAP Unicode RFC SDK (librfc32u.dll) 的 64 位元或 32 位元版本的 SAP 系統與通訊。 

下圖顯示使用開發的解決方案的端對端架構[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
 ![SAP 端&#45;到&#45;結束架構](../../adapters-and-accelerators/adapter-sap/media/9ba0c31f-90df-444d-8192-42743c893d51.gif "9ba0c31f-90df-444d-8192-42743c893d51")  
  
## <a name="consuming-the-adapter"></a>使用配接器  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]公開 （expose) 為 SAP 系統[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務用戶端應用程式。 用戶端應用程式交換的 SOAP 訊息[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]管道可執行作業，而且存取 SAP 系統上的資料。 上圖顯示四種方式，在其中[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可取用。  
  
- 透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道執行 SAP 系統上的作業所使用的應用程式[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型來交換 SOAP 訊息直接與[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 如需開發解決方案的詳細資訊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]利用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型程式設計，請參閱[使用 WCF 通道模型開發應用程式](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)。  
  
- 透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務呼叫方法的模型應用程式[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]SAP 系統上執行作業的用戶端。 A[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端模型所公開之作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]為.NET 方法。 您可以使用[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]或 svcutil.exe 工具來建立[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端類別所公開的中繼資料從[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 如需詳細資訊[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型程式設計和[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[使用 WCF 服務模型開發應用程式](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)。  
  
- 透過 BizTalk 連接埠設定為使用 BizTalk WCF 自訂配接器與 SAP 繫結設定為 Wcf-custom 傳輸類型中的繫結[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式。 BizTalk Wcf-custom 配接器之間進行通訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式和[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務。 BizTalk Wcf-custom 配接器支援自訂[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]透過 WCF 自訂繫結的傳輸類型，可讓您設定任何[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]向組態系統公開為 BizTalk Wcf-custom 配接器所使用的繫結的繫結。 如需有關如何使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案，請參閱[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)。 BizTalk 交易支援，可以藉由設定 SAP 繫結的繫結屬性將其載入 BizTalk 分層通道繫結項目。  
  
- 透過 IIS 裝載的 Web 服務。 在此案例中，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]透過公開[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務的 proxy，裝載於 IIS 使用其中一種標準[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]HTTP 繫結。  
  
- 透過[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]。 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]之上執行[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]並提供到 SAP 系統的 ADO.NET 介面。  
  
  [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]和 SAP RFC 程式庫永遠裝載同處理序的應用程式或取用配接器的服務。  
  
## <a name="sap-adapter-and-wcf"></a>SAP 配接器和 WCF  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] 提供程式設計模型，根據用戶端與服務之間的通道上的 SOAP 訊息交換。 通訊的用戶端和服務所公開的端點之間傳送這些訊息。  
  
 端點所組成*端點位址*指定處接收訊息的位置*繫結*指定用來交換訊息，以及的通訊協定*合約*指定端點所公開的作業和資料類型。 繫結是由堆疊在彼此的上層定義與端點交換訊息的方式的一或多個繫結項目所組成。  
  
 最少的傳輸和編碼用來與端點交換訊息，必須指定繫結。 端點之間交換訊息是透過通道堆疊所組成的一或多個通道。 每個通道是其中一個繫結項目，設定端點的繫結中的具象實作。  
  
[WCF 文件](http://go.microsoft.com/fwlink/?LinkID=196850)包含更多詳細資料，關於[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，和[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]程式設計模型。  
  
 [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]公開[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]自訂繫結，SAP 繫結 (**Microsoft.Adapters.SAP.SAPBinding**)。 根據預設，此繫結包含單一的自訂傳輸繫結項目，SAP 配接器繫結項目 (**Microsoft.Adapters.SAP.SAPAdapter**)，可讓 SAP 系統上的作業。 使用時[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以設定**EnableBizTalkCompatibilityMode**載入自訂繫結項目，BizTalk 分層通道繫結項目，在 SAP 配接器繫結上的屬性繫結項目。 BizTalk 分層通道繫結項目在內部實作[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，不會公開外部 SAP 繫結。  
  
 **Microsoft.Adapters.SAP.SAPBinding** （SAP 繫結） 和**Microsoft.Adapters.SAP.SAPAdapter** （SAP 配接器繫結項目） 是公用的類別，也會公開至組態系統。 SAP 配接器繫結項目公開的因為您可以建置自己的自訂[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]繫結的擴充功能的支援[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 例如，您可以實作以支援企業單一登入 (SSO) 中的自訂繫結[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道或[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型程式設計方案，來彙總的資料庫作業為單一多功能的作業，或執行自訂的應用程式所實作的作業與 SAP 系統上的作業之間的結構描述轉換。  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]建置的上方[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]之上執行和[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]執行階段。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供軟體架構和工具的基礎結構[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]利用提供給使用者和配接器用戶端的一組豐富的功能。  

## <a name="sap-adapter-and-the-wcf-lob-adapter-sdk"></a>SAP 配接器和 WCF LOB 配接器 SDK
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]會實作一組核心元件，利用所提供的功能[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，並提供給透過 SAP Unicode RFC SDK 程式庫 (librfc32u.dll) 部署 SAP 系統的連線。  
  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]做為透過此軟體層[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]介面[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]，並做為透過此層的 RFC SDK[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與 SAP 系統的介面。 下圖顯示的內部元件之間的關聯性[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]之間以及這些元件與 RFC SDK。  
  
 ![內部配接器元件的關係](../../adapters-and-accelerators/adapter-sap/media/10f97b95-4e82-4592-ba07-0f58478305c2.gif "10f97b95-4e82-4592-ba07-0f58478305c2")  
  
## <a name="connection-to-the-sap-system"></a>連接到 SAP 系統  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與 SAP 系統，透過 SAP Unicode RFC SDK 程式庫 (librfc32u.dll) 連線。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援 32 位元和 64 位元版本的 SAP RFC SDK。 SAP RFC SDK 可讓 SAP 系統上呼叫 ABAP 函式的外部程式。  
  
 您連接到 SAP 系統所提供的連線 URI 以[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援下列類型的 SAP 系統的連線：  
  
- 應用程式主機型連線 (A)，在其中[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]直接連接到 SAP 應用程式伺服器。  
  
- 負載平衡連線 (B)，在其中[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]連接到 SAP 訊息伺服器。  
  
- 目的地為基礎的連接 (D)，SAP 系統的連線由 saprfc.ini 組態檔中的目的地。 A、 B 和 R 支援類型的連線。  
  
- Rfc、 tRFC 和透過上所指定的接聽程式的主應用程式，接聽程式閘道服務和接聽程式的程式識別碼，直接在 連線 URI 中或是以 R 為基礎的 SAP 系統的 RFC 目的地的 Idoc，配接器的接收接聽程式連接 (R)saprfc.ini 組態檔中的目的地。  
  
  如需有關 saprfc.ini 檔案的詳細資訊，請參閱 「 SAPRFC。中的 INI 檔案 」 [SAP 文件](https://help.sap.com/doc/PRODUCTION/saphelp_nwpi711/7.1.1/en-US/48/c4168eca64581de10000000a42189c/frameset.htm)。  
  
  如需有關如何[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]連接到 SAP 系統，請參閱[建立 SAP 系統的連線](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md)。  
  
## <a name="see-also"></a>另請參閱  
 [了解 BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)