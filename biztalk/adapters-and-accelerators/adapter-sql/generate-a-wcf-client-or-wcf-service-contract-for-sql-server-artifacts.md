---
title: 產生 WCF 用戶端或 WCF 服務合約的 SQL Server 成品 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5fa7d8c0-8ee4-41e7-9394-d22e87e09391
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0930baa5ec89c500f15a5ae7a88ce36e71785c96
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013335"
---
# <a name="generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts"></a>SQL Server 成品的產生 WCF 用戶端或 WCF 服務合約
您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]以產生 WCF 用戶端類別作為目標的 SQL Server 成品中選取的作業。 您也可以使用 ServiceModel Metadata Utility Tool (svcutil.exe)，以產生 WCF 用戶端類別;不過，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]公開 ServiceModel Metadata Utility Tool，透過標準的 Microsoft Windows 介面的功能。 它也提供不是使用 svcutil.exe 工具，可用的瀏覽和搜尋功能，並產生組態檔，根據您選取當您連接到 SQL Server 資料庫的繫結屬性。  
  
## <a name="generating-a-wcf-client-class-by-using-the-add-adapter-service-reference-plug-in"></a>產生 WCF 用戶端類別，使用 新增配接器服務參考外掛程式  
 執行下列步驟以產生 WCF 用戶端類別使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
1. 在 [[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]方案總管] 中，以滑鼠右鍵按一下您的專案，然後**新增配接器服務參考**。  
  
2. 之後**新增配接器服務參考** 對話方塊隨即開啟，請依照中的步驟[取得 Visual Studio 中使用 SQL 配接器中的 SQL Server 作業的中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)連接到 SQL Server，並瀏覽和搜尋作業。 若要建立的作業，您選取的 WCF 用戶端類別，務必**用戶端 （傳出作業）** 從選取**選取合約的型別**下拉式清單。 （這是預設值）。  
  
3. 選取所有您想要為目標，請按一下作業後**確定**來產生 WCF 用戶端類別。  
  
   [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將兩個檔案新增至您的專案：  
  
- **WCF 用戶端程式碼檔**。 此檔案包含 WCF 用戶端類別和協助程式程式碼產生您所選取的作業。 第一次執行[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，它會產生此檔案的預設名稱**SQLAdapterBindingClient.cs**。 如果您再次執行它，它會產生下一個檔案將會呼叫**SQLAdapterBindingClient1.cs**。  數字尾碼會增加 1，如您所產生的每個新檔案。  您也可以變更預設前置詞**SQLBinding**輸入中的不同前置詞**檔案名稱前置詞**欄位[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]然後再選取**確定**至產生的檔案。  
  
- **App.config**。此檔案包含的繫結組態和設定的連接時所做的選取項目為基礎的用戶端端點組態[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
  > [!IMPORTANT]
  >  同時使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，如果您未指定的字串類型的繫結屬性的值，而其預設值是 null，則該屬性繫結將無法使用 app.config 檔案中。 您必須手動加入的繫結屬性和其值在 app.config 檔案中，如有必要。  
  
## <a name="generating-a-wcf-service-contract-by-using-the-add-adapter-service-reference-plug-in"></a>使用產生的 WCF 服務合約加入配接器服務參考外掛程式  
 輪詢 SQL Server 資料庫，或從資料庫中，接收通知等的輸入作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]執行 （如果是輪詢） 用戶端應用程式所指定的查詢，或向 （中的案例中的 SQL Server 中的查詢通知）。 在這兩個案例中，配接器會傳送內送的訊息，從 SQL Server 資料庫來使用。 在此情況下，取用方應用程式做為服務和[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]做為用戶端。 您必須，因此，實作 WCF 服務，可從配接器接收輸入的作業。 若要這樣做，您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來產生代表服務合約是配接器的輸入作業所呈現的.NET 介面。 此.NET 介面也會呼叫 WCF 服務合約。 然後，您會實作這個介面可建立的 WCF 服務，您可以使用來接收輸入的作業。  
  
 執行下列步驟，以使用產生的 WCF 服務合約[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-generate-a-wcf-service-contract-for-inbound-operations"></a>若要產生的輸入作業的 WCF 服務合約  
  
1. 在 [[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]方案總管] 中，以滑鼠右鍵按一下您的專案，然後**新增配接器服務參考**。  
  
2. 之後**新增配接器服務參考** 對話方塊隨即開啟，請依照中的步驟[連接到 SQL Server，在 Visual Studio 使用新增配接器服務參考外掛程式](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-add-adapter-service-reference.md)來連接到 SQL Server 資料庫。  
  
   > [!IMPORTANT]
   >  如果您要產生的 WCF 服務合約**TypedPolling**輸入的作業，您必須指定**InboundID**連線 URI 的一部分並**PollingStatement**繫結屬性。  
  
3. 您已經連接到 SQL Server 資料庫之後，請選取**服務 （輸入作業）** 從**選取合約的型別**下拉式清單。  
  
4. 在**選取類別目錄**方塊中，按一下 [根] 節點 (**/**)，選取的輸入的作業**可用分類和作業**] 方塊中，然後按一下 [**新增**。  
  
5. 若要產生的輸入作業的 WCF 服務合約，請按一下**確定**。  
  
   [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將三個檔案新增至您的專案：  
  
- **SqlAdapterBindingInterface.cs**。 此檔案包含產生的 WCF 服務合約 （介面），並輸入作業的協助程式程式碼。  
  
- **SqlAdapterBindingService.cs**。 此檔案包含實作 SqlAdapterBindingInterface.cs 中定義的介面的類別。 您可以實作商務邏輯，以處理輸入作業所傳回的記錄。  
  
- **App.config**。此檔案包含繫結組態、 端點行為，以及您設定的繫結和連線時所做的選取項目為基礎的服務端點組態[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
  > [!IMPORTANT]
  >  同時使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，如果您未指定的字串類型的繫結屬性的值，而其預設值是 null，則該屬性繫結將無法使用 app.config 檔案中。 您必須手動加入的繫結屬性和其值在 app.config 檔案中，如有必要。  
  
## <a name="generating-a-wcf-client-class-by-using-svcutilexe"></a>使用 svcutil.exe 產生 WCF 用戶端類別  
 您可以使用 svcutil.exe 來產生 WCF 用戶端類別，您的應用程式。 您必須設定與 svcutil.exe [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
 Svcutil.exe 產生 WCF 用戶端類別中的預設檔案名稱的輸出檔案**output.cs**。 您必須手動將此檔案中的您[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案。 如需 svcutil.exe 的詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)。
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)