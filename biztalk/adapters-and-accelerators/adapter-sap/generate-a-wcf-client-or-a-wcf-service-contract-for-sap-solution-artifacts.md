---
title: 產生 WCF 用戶端或 SAP 方案成品的 WCF 服務合約 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff01e2b0-6480-427a-bc6d-6169e7d6e256
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 035f1263922a0c455662139ca112794e920e3848
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217494"
---
# <a name="generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts"></a>產生 WCF 用戶端或 SAP 方案成品的 WCF 服務合約
您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別或選取 SAP 成品作業目標的 WCF 服務合約 （介面）。 您也可以使用 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別或 WCF 服務合約。不過，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]公開 ServiceModel Metadata Utility Tool，透過標準的 Microsoft Windows 介面的功能。 它也提供不是使用 svcutil.exe 工具，可用的瀏覽和搜尋功能，並產生根據您選取當您連接到 SAP 系統的繫結屬性的組態檔。  
  
## <a name="generating-a-client-class-by-using-the-add-adapter-service-reference-plug-in"></a>使用產生的用戶端類別新增配接器服務參考外掛程式  
 執行下列步驟來產生 WCF 用戶端類別使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-generate-a-wcf-client-class"></a>若要產生 WCF 用戶端類別  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]方案總管 中，以滑鼠右鍵按一下您的專案，然後**新增配接器服務參考**。  
  
2.  之後**新增配接器服務參考**對話方塊隨即開啟，請依照下列中的步驟[取得 Visual Studio 中的 SAP 作業的中繼資料](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)連接到 SAP 系統和瀏覽和搜尋作業。 若要建立的作業，您選取的 WCF 用戶端類別，務必**用戶端 （輸出作業）** 選取從**選取合約型別**下拉式清單 （這是預設值）。  
  
3.  在您選取的所有作業，您要為目標，請按一下之後**確定**產生 WCF 用戶端類別。  
  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將兩個檔案加入至您的專案：  
  
-   **SAPBindingClient.cs**。 此檔案包含 WCF 用戶端類別和協助程式程式碼產生您所選取的作業。  
  
-   **App.config**。此檔案包含的繫結組態和用戶端端點組態。 設定會依據您先前設定的繫結和連接時，您所選項目[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
    > [!IMPORTANT]
    >  同時使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，如果您未指定類型字串的繫結屬性的值，且其預設值為 null 然後，繫結屬性將不會使用 app.config 檔案中。 您必須以手動方式繫結屬性和其值在 app.config 檔案中，視需要新增。  
  
## <a name="generating-a-wcf-service-contract-by-using-the-add-adapter-service-reference-plug-in"></a>使用產生的 WCF 服務合約加入服務參考外掛程式配接器  
 當您使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]若要從 SAP 系統接收 Idoc，Rfc，tRFCs，您的程式碼可做為配接器的服務。 也就是說，配接器收到來自 SAP 系統的適當成品，然後再叫用您的程式碼傳遞至您的應用程式的成品 （輸入） 作業。  
  
 您必須，因此，實作 WCF 服務可從配接器接收輸入這項作業。 若要這樣做，您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生代表服務合約之作業的配接器會顯示.NET 介面。 這個.NET 介面也稱為 WCF 服務合約。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生包含 WCF 服務的 stub 的實作的類別。 然後，您會實作這個介面可建立 WCF 服務可讓您接收作業。  
  
 執行下列步驟來產生 WCF 服務合約使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-generate-a-wcf-service-contract"></a>若要產生 WCF 服務合約  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]方案總管 中，以滑鼠右鍵按一下您的專案，然後**新增配接器服務參考**。  
  
2.  之後**新增配接器服務參考**對話方塊隨即開啟，請依照下列中的步驟[取得 Visual Studio 中的 SAP 作業的中繼資料](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)連接到 SAP 系統和瀏覽和搜尋作業。 若要建立 WCF 服務合約，您選取的作業，務必**服務 （輸入操作）** 選取從**選取合約型別**下拉式清單。  
  
3.  在您選取的所有作業，您要為目標，請按一下之後**確定**產生 WCF 服務合約。  
  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將三個檔案加入至您的專案：  
  
-   **SAPBindingInterface.cs**。 這個檔案包含產生的 WCF 服務合約 （介面），並針對您選取作業的協助程式程式碼。  
  
-   **SAPBindingService.cs**。 此檔案包含 stub 的 WCF 服務類別可實作 SAPBindingInterface.cs 中定義的介面。 您可以實作商務邏輯處理 RFC、 tRFC 或 IDOC，直接在這個類別的方法。  
  
-   **App.config**。此檔案包含的繫結組態、 端點行為，以及您所做設定的繫結和連接時的選擇為基礎的服務端點組態[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
    > [!IMPORTANT]
    >  同時使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，如果您未指定類型字串的繫結屬性的值，且其預設值為 null 然後，繫結屬性將不會使用 app.config 檔案中。 您必須以手動方式繫結屬性和其值在 app.config 檔案中，視需要新增。  
  
> [!NOTE]
>  您沒有指定的 RFC 伺服器參數，當您設定連線 URI 的[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 WCF 服務合約。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]擷取中繼資料從 SAP 系統，透過用戶端連線。  
  
## <a name="generate-a-wcf-client-class-or-a-wcf-service-contract-by-using-svcutilexe"></a>使用 svcutil.exe 產生 WCF 用戶端類別或 WCF 服務合約  
 您可以使用 svcutil.exe 產生 WCF 用戶端類別或 WCF 服務合約，您的應用程式。 您必須設定要搭配使用 svcutil.exe [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 如需有關設定和使用具有 svcutil.exe [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[mySAP Business Suite 與 BizTalk 配接器使用 ServiceModel Metadata Utility Tool](../../adapters-and-accelerators/adapter-sap/use-the-servicemodel-metadata-utility-with-the-sap-adapter-in-biztalk.md)。  
  
 Svcutil.exe 會產生 WCF 用戶端類別或 WCF 服務合約中的輸出檔。 預設檔案名稱是 output.cs。 您必須手動加入這個檔案中的您[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案。  
  
## <a name="see-also"></a>另請參閱  
[開發 SAP 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)