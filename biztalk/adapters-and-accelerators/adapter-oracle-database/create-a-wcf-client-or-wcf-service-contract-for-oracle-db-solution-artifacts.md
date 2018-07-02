---
title: 產生 WCF 用戶端或 Oracle 資料庫解決方案成品的 WCF 服務合約 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model programming, creating a proxy
- how to, create a proxy
- creating a proxy
- proxy programming, creating a proxy
ms.assetid: 3e832ae9-e253-4476-9f25-8cf0de12f469
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1e042fb8a60953996f4651d4a4397f75a264e32
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967503"
---
# <a name="generate-a-wcf-client-or-a-wcf-service-contract-for-oracle-database-solution-artifacts"></a>產生 WCF 用戶端或 Oracle 資料庫解決方案成品的 WCF 服務合約
您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]來產生 WCF 用戶端類別，或者目標為選取的作業上 Oracle 資料庫成品的 WCF 服務合約 （介面）。 您也可以使用 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別或 WCF 服務合約。不過，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]公開 ServiceModel Metadata Utility Tool，透過標準的 Microsoft Windows 介面的功能。 它也提供不是使用 svcutil.exe 工具，可用的瀏覽和搜尋功能，並產生組態檔，根據您選取當您連接到 Oracle 資料庫的繫結屬性。  
  
## <a name="generating-a-client-class-by-using-the-add-adapter-service-reference-plug-in"></a>使用產生的用戶端類別新增配接器服務參考外掛程式  
 執行下列步驟以產生 WCF 用戶端類別使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-generate-a-wcf-client-class"></a>若要產生 WCF 用戶端類別  
  
1. 在 [[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]方案總管] 中，以滑鼠右鍵按一下您的專案，然後**新增配接器服務參考**。  
  
2. 在後**新增配接器服務參考** 對話方塊隨即開啟，請依照中的步驟[擷取 Oracle 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)連接到 Oracle 資料庫並瀏覽和搜尋作業。 若要建立的作業，您選取的 WCF 用戶端類別，務必**用戶端 （傳出作業）** 從選取**選取合約的型別**（這是預設值） 的下拉式清單。  
  
3. 選取所有您想要為目標，請按一下作業後**確定**來產生 WCF 用戶端類別。  
  
   [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將兩個檔案新增至您的專案：  
  
- **OracleDBBindingClient.cs**。 此檔案包含 WCF 用戶端類別和協助程式程式碼產生您所選取的作業。  
  
- **App.config**。此檔案包含的繫結組態和用戶端端點組態。 這些設定會根據您設定的繫結和連線時所做的選取項目[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
  > [!IMPORTANT]
  >  同時使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，如果您未指定的字串類型的繫結屬性的值，而其預設值是 null，則該屬性繫結將無法使用 app.config 檔案中。 您必須手動加入的繫結屬性和其值在 app.config 檔案中，如有必要。  
  
## <a name="generating-a-wcf-service-contract-by-using-the-add-adapter-service-reference-plug-in"></a>使用產生的 WCF 服務合約加入配接器服務參考外掛程式  
 配接器會公開，讓 Oracle 資料庫，可以將訊息傳送至配接器的用戶端的輸入的作業。 針對這類作業，您必須產生的 WCF 服務合約。 例如，配接器會顯示輸入的 POLLINGSTMT 作業來輪詢 Oracle 資料庫。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]執行查詢所指定**PollingStatement**繫結屬性和結果集 POLLINGSTMT 訊息中取用中應用程式的傳送。 在此案例中，取用方應用程式做為服務和[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]做為用戶端。 您必須，因此，實作 WCF 服務可從配接器接收 POLLINGSTMT 作業。 若要這樣做，您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來產生代表服務合約是呈現 POLLINGSTMT 作業的配接器的.NET 介面。 此.NET 介面也會呼叫 WCF 服務合約。 然後，您會實作這個介面可建立的 WCF 服務，您可以使用來接收 POLLINGSTMT 作業。  
  
 本節提供有關如何產生 WCF 服務合約使用的資訊[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]的輸入配接器所公開的作業。  
  
#### <a name="to-generate-a-wcf-service-contract-for-inbound-operations"></a>若要產生的輸入作業的 WCF 服務合約  
  
1. 在 [[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]方案總管] 中，以滑鼠右鍵按一下您的專案，然後**新增配接器服務參考**。  
  
2. 在後**新增配接器服務參考** 對話方塊隨即開啟，請依照中的步驟[擷取 Oracle 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)來連接到 Oracle 資料庫。 有數個繫結屬性和一個 URI 屬性，您可能想要設定當您連接到 Oracle 資料庫的輸入作業。 例如，針對輸入的輪詢作業 (**POLLINGSTMT**)，您必須指定**PollingStatement**繫結屬性，當您設定 Oracle 資料庫的連接。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]來產生代表 POLLINGSTMT 作業所傳回的結果集的類別會使用這個屬性中指定的 SQL SELECT 陳述式。  
  
3. 您已經連接到 Oracle 資料庫之後，請選取**服務 （輸入作業）** 從**選取合約的型別**下拉式清單。  
  
4. 在 **選取一個類別**方塊中，按一下 根 節點 (**/**)，並瀏覽至您要用來產生服務合約的作業。 例如，輪詢作業中，選取**POLLINGSTMT**從**可用的類別和作業**方塊，然後再按一下**新增**。  
  
5. 若要產生 POLLINGSTMT 作業的 WCF 服務合約，請按一下**確定**。  
  
   [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將三個檔案新增至您的專案：  
  
- **OracleDBBindingInterface.cs**。 此檔案包含產生的 WCF 服務合約 （介面） 和 POLLINGSTMT 作業的協助程式程式碼。  
  
- **OracleDBBindingService.cs**。 此檔案包含實作 OracleDBBindingInterface.cs 中定義的介面的類別。 您可以實作商務邏輯，以處理在 POLLINGSTMT 方法中，此類別中，輪詢查詢所傳回的記錄。  
  
- **App.config**。此檔案包含繫結組態、 端點行為，以及您設定的繫結和連線時所做的選取項目為基礎的服務端點組態[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
  > [!IMPORTANT]
  >  同時使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，如果您未指定的字串類型的繫結屬性的值，而其預設值是 null，則該屬性繫結將無法使用 app.config 檔案中。 您必須手動加入的繫結屬性和其值在 app.config 檔案中，如有必要。  
  
## <a name="using-svcutilexe-to-generate-a-wcf-client-class-or-a-wcf-service-contract"></a>使用 svcutil.exe 產生 WCF 用戶端類別或 WCF 服務合約  
 您可以使用 svcutil.exe 來產生 WCF 用戶端類別或 WCF 服務介面，您的應用程式。 您必須設定與 svcutil.exe [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 如需有關設定及使用具有 svcutil.exe [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 < [ServiceModel Metadata Utility Tool 與 BizTalk 配接器用於 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/use-the-servicemodel-metadata-utility-with-the-oracle-db-adapter-in-biztalk.md)。  
  
 Svcutil.exe 會產生 WCF 用戶端類別或 WCF 服務合約中的輸出檔。 預設檔案名稱是 output.cs。 您必須手動將此檔案中的您[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案。  
  
## <a name="see-also"></a>另請參閱  
 [使用 WCF 服務模型開發 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)   
 [在 SQL 中使用 WCF 服務模型執行基本 Insert、 Update、 Delete 和 Select 作業](../../adapters-and-accelerators/adapter-sql/insert-update-delete-or-select-operations-in-sql-using-the-wcf-service-model.md)