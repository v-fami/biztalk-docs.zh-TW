---
title: 產生 WCF 用戶端或 SAP 解決方案成品的 WCF 服務合約 |Microsoft Docs
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
ms.openlocfilehash: 817a76abac05c76e67edf03168f596eb999b5ee4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981351"
---
# <a name="generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts"></a>產生 WCF 用戶端或 SAP 解決方案成品的 WCF 服務合約
您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]來產生 WCF 用戶端類別，或者在選取 SAP 成品的作業為目標的 WCF 服務合約 （介面）。 您也可以使用 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別或 WCF 服務合約。不過，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]公開 ServiceModel Metadata Utility Tool，透過標準的 Microsoft Windows 介面的功能。 它也提供不是使用 svcutil.exe 工具，可用的瀏覽和搜尋功能，並產生組態檔，根據您選取當您連接到 SAP 系統的繫結屬性。  
  
## <a name="generating-a-client-class-by-using-the-add-adapter-service-reference-plug-in"></a>使用產生的用戶端類別新增配接器服務參考外掛程式  
 執行下列步驟以產生 WCF 用戶端類別使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-generate-a-wcf-client-class"></a>若要產生 WCF 用戶端類別  
  
1. 在 [[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]方案總管] 中，以滑鼠右鍵按一下您的專案，然後**新增配接器服務參考**。  
  
2. 之後**新增配接器服務參考** 對話方塊隨即開啟，請依照中的步驟[取得 SAP 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)來連接到 SAP 系統和瀏覽和搜尋作業。 若要建立的作業，您選取的 WCF 用戶端類別，務必**用戶端 （傳出作業）** 從選取**選取合約的型別**（這是預設值） 的下拉式清單。  
  
3. 選取所有您想要為目標，請按一下作業後**確定**來產生 WCF 用戶端類別。  
  
   [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將兩個檔案新增至您的專案：  
  
- **SAPBindingClient.cs**。 此檔案包含 WCF 用戶端類別和協助程式程式碼產生您所選取的作業。  
  
- **App.config**。此檔案包含的繫結組態和用戶端端點組態。 設定會根據您設定的繫結和連線時所做的選取項目[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
  > [!IMPORTANT]
  >  同時使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，如果您未指定的字串類型的繫結屬性的值，而其預設值是 null，則該屬性繫結將無法使用 app.config 檔案中。 您必須手動加入的繫結屬性和其值在 app.config 檔案中，如有必要。  
  
## <a name="generating-a-wcf-service-contract-by-using-the-add-adapter-service-reference-plug-in"></a>使用產生的 WCF 服務合約加入配接器服務參考外掛程式  
 當您使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]若要從 SAP 系統接收 Idoc，Rfc、 Trfc，您的程式碼可做為配接器的服務。 也就是配接器從 SAP 系統接收適當的成品，然後再叫用您的程式碼，將您的應用程式的成品 （輸入） 作業。  
  
 您必須，因此，實作 WCF 服務可從配接器接收輸入這項作業。 若要這樣做，您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來產生代表服務合約是作業的配接器中呈現的.NET 介面。 此.NET 介面也會呼叫 WCF 服務合約。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生包含附加虛設常式的實作的 WCF 服務的類別。 然後，您會實作這個介面可建立的 WCF 服務，您可以使用來接收作業。  
  
 執行下列步驟，以使用產生的 WCF 服務合約[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-generate-a-wcf-service-contract"></a>若要產生的 WCF 服務合約  
  
1. 在 [[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]方案總管] 中，以滑鼠右鍵按一下您的專案，然後**新增配接器服務參考**。  
  
2. 之後**新增配接器服務參考** 對話方塊隨即開啟，請依照中的步驟[取得 SAP 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)來連接到 SAP 系統和瀏覽和搜尋作業。 若要建立的 WCF 服務合約，如您所選取的作業，務必**服務 （輸入作業）** 從選取**選取合約的型別**下拉式清單。  
  
3. 選取所有您想要為目標，請按一下作業後**確定**來產生 WCF 服務合約。  
  
   [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將三個檔案新增至您的專案：  
  
- **SAPBindingInterface.cs**。 此檔案包含產生的 WCF 服務合約 （介面），並協助程式程式碼，如您所選取的作業。  
  
- **SAPBindingService.cs**。 此檔案包含附加虛設常式的 WCF 服務類別可實作 SAPBindingInterface.cs 中定義的介面。 您可以實作處理 RFC、 tRFC 或 IDOC，直接在這個類別的方法中的商務邏輯。  
  
- **App.config**。此檔案包含繫結組態、 端點行為，以及您設定的繫結和連線時所做的選取項目為基礎的服務端點組態[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
  > [!IMPORTANT]
  >  同時使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，如果您未指定的字串類型的繫結屬性的值，而其預設值是 null，則該屬性繫結將無法使用 app.config 檔案中。 您必須手動加入的繫結屬性和其值在 app.config 檔案中，如有必要。  
  
> [!NOTE]
>  您沒有指定 RFC 伺服器參數，當您設定的連線 URI 的[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來產生 WCF 服務合約。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]擷取中繼資料從 SAP 系統，透過用戶端連線。  
  
## <a name="generate-a-wcf-client-class-or-a-wcf-service-contract-by-using-svcutilexe"></a>使用 svcutil.exe 產生 WCF 用戶端類別或 WCF 服務合約  
 您可以使用 svcutil.exe 來產生 WCF 用戶端類別或 WCF 服務合約，為您的應用程式。 您必須設定與 svcutil.exe [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 如需有關設定及使用具有 svcutil.exe [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱 <<c2> [ 使用 ServiceModel Metadata Utility Tool 與 BizTalk Adapter mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-servicemodel-metadata-utility-with-the-sap-adapter-in-biztalk.md)。  
  
 Svcutil.exe 會產生 WCF 用戶端類別或 WCF 服務合約中的輸出檔。 預設檔案名稱是 output.cs。 您必須手動將此檔案中的您[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案。  
  
## <a name="see-also"></a>另請參閱  
[開發使用 WCF 通道模型的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)