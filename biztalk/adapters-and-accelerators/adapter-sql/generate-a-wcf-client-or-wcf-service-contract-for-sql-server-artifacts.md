---
title: "SQL Server 成品產生 WCF 用戶端或 WCF 服務合約 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fa7d8c0-8ee4-41e7-9394-d22e87e09391
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f961c3648e153847f5ac259c9902da5589b1486d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts"></a>SQL Server 成品產生 WCF 用戶端或 WCF 服務合約
您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別針對選取的作業，於 SQL Server 成品上指明。 您也可以使用 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別。不過，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]公開 ServiceModel Metadata Utility Tool，透過標準的 Microsoft Windows 介面的功能。 它也提供不是使用 svcutil.exe 工具，可用的瀏覽和搜尋功能，並產生根據您連接到 SQL Server 資料庫時，您選取的繫結屬性的組態檔。  
  
## <a name="generating-a-wcf-client-class-by-using-the-add-adapter-service-reference-plug-in"></a>使用產生 WCF 用戶端類別新增配接器服務參考外掛程式  
 執行下列步驟來產生 WCF 用戶端類別使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]方案總管 中，以滑鼠右鍵按一下您的專案，然後**新增配接器服務參考**。  
  
2.  之後**新增配接器服務參考**對話方塊隨即開啟，請依照下列中的步驟[取得中繼資料使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)連線到 SQL Server，並瀏覽和搜尋作業。 若要建立的作業，您選取的 WCF 用戶端類別，務必**用戶端 （輸出作業）**選取從**選取合約型別**下拉式清單。 （這是預設值）。  
  
3.  在您選取的所有作業，您要為目標，請按一下之後**確定**產生 WCF 用戶端類別。  
  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將兩個檔案加入至您的專案：  
  
-   **WCF 用戶端程式碼檔**。 此檔案包含 WCF 用戶端類別和協助程式程式碼產生您所選取的作業。 第一次執行[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，它會產生這個檔案的預設名稱**SQLAdapterBindingClient.cs**。 如果您再次執行它，它會產生的下一個檔案將會呼叫**SQLAdapterBindingClient1.cs**。  數字尾碼會增加 1 的每一個您所產生的新檔案。  您也可以變更預設前置詞**SQLBinding**輸入中的不同前置詞**檔案名稱前置詞**欄位[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]前，先選取**確定**至產生的檔案。  
  
-   **App.config**。這個檔案包含的繫結組態和設定的連接時所做的選擇為基礎的用戶端端點組態[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
    > [!IMPORTANT]
    >  同時使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，如果您未指定類型字串的繫結屬性的值，且其預設值為 null 然後，繫結屬性將不會使用 app.config 檔案中。 您必須以手動方式繫結屬性和其值在 app.config 檔案中，視需要新增。  
  
## <a name="generating-a-wcf-service-contract-by-using-the-add-adapter-service-reference-plug-in"></a>使用產生的 WCF 服務合約加入服務參考外掛程式配接器  
 輸入的作業，例如輪詢 SQL Server 資料庫，或從資料庫中，接收通知的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]執行 （如果是輪詢） 用戶端應用程式所指定的查詢或查詢登錄 （中的案例中的 SQL server通知）。 在這兩個案例中，配接器會傳送 SQL Server 資料庫來使用內送的訊息。 在這種情況下，使用應用程式做為服務和[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]做為用戶端。 您必須，因此，實作 WCF 服務可以接收來自配接器的輸入的操作。 若要這樣做，您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生一個.NET 介面，表示會顯示輸入操作的配接器的服務合約。 這個.NET 介面也稱為 WCF 服務合約。 然後，您會實作這個介面可建立 WCF 服務，您可以使用來接收傳入的作業。  
  
 執行下列步驟來產生 WCF 服務合約使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-generate-a-wcf-service-contract-for-inbound-operations"></a>若要產生 WCF 服務合約的輸入作業  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]方案總管 中，以滑鼠右鍵按一下您的專案，然後**新增配接器服務參考**。  
  
2.  之後**新增配接器服務參考**對話方塊隨即開啟，請依照下列中的步驟[連接到 Visual Studio 使用加入配接器服務參考外掛程式中的 SQL Server](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-add-adapter-service-reference.md)連接到 SQL Server 資料庫。  
  
    > [!IMPORTANT]
    >  如果您要產生 WCF 服務合約**TypedPolling**輸入的作業，您必須指定**InboundID**連線 URI 的一部分和**PollingStatement**繫結屬性。  
  
3.  您已經連接到 SQL Server 資料庫之後，請選取**服務 （輸入操作）**從**選取合約型別**下拉式清單。  
  
4.  在**選取類別目錄**方塊中，按一下根節點 (**/**)，選取的輸入的作業**可用的類別和作業** 方塊中，然後按一下**新增**。  
  
5.  若要產生輸入作業的 WCF 服務合約，請按一下**確定**。  
  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將三個檔案加入至您的專案：  
  
-   **SqlAdapterBindingInterface.cs**。 這個檔案包含產生的 WCF 服務合約 （介面），並輸入作業的協助程式程式碼。  
  
-   **SqlAdapterBindingService.cs**。 此檔案包含實作介面 SqlAdapterBindingInterface.cs 中定義的類別。 您可以實作商務邏輯來處理輸入作業所傳回的記錄。  
  
-   **app.config**。此檔案包含的繫結組態、 端點行為，以及您所做設定的繫結和連接時的選擇為基礎的服務端點組態[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
    > [!IMPORTANT]
    >  同時使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，如果您未指定類型字串的繫結屬性的值，且其預設值為 null 然後，繫結屬性將不會使用 app.config 檔案中。 您必須以手動方式繫結屬性和其值在 app.config 檔案中，視需要新增。  
  
## <a name="generating-a-wcf-client-class-by-using-svcutilexe"></a>使用 svcutil.exe 產生 WCF 用戶端類別  
 您可以使用 svcutil.exe 產生 WCF 用戶端類別，您的應用程式。 您必須設定要搭配使用 svcutil.exe [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
 Svcutil.exe 產生 WCF 用戶端類別中的預設檔案名稱的輸出檔**output.cs**。 您必須手動加入這個檔案中的您[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案。 如需 svcutil.exe 的詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)。
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)