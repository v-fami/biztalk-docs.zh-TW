---
title: 產生 WCF 用戶端或 Oracle 資料庫方案成品的 WCF 服務合約 |Microsoft 文件
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
ms.openlocfilehash: e729adec26aca98df80ecc7917ab0558faa6632e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215886"
---
# <a name="generate-a-wcf-client-or-a-wcf-service-contract-for-oracle-database-solution-artifacts"></a>產生 WCF 用戶端或 Oracle 資料庫方案成品的 WCF 服務合約
您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別或 WCF 服務合約 （介面） 為目標的 Oracle 資料庫成品中選取的作業。 您也可以使用 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別或 WCF 服務合約。不過，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]公開 ServiceModel Metadata Utility Tool，透過標準的 Microsoft Windows 介面的功能。 它也提供不是使用 svcutil.exe 工具，可用的瀏覽和搜尋功能，並在產生組態檔，根據您連接到 Oracle 資料庫時，您選取的繫結屬性。  
  
## <a name="generating-a-client-class-by-using-the-add-adapter-service-reference-plug-in"></a>使用產生的用戶端類別新增配接器服務參考外掛程式  
 執行下列步驟來產生 WCF 用戶端類別使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-generate-a-wcf-client-class"></a>若要產生 WCF 用戶端類別  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]方案總管 中，以滑鼠右鍵按一下您的專案，然後**新增配接器服務參考**。  
  
2.  之後**新增配接器服務參考**對話方塊隨即開啟，請依照下列中的步驟[擷取 Oracle 作業在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)連接到 Oracle 資料庫並瀏覽及搜尋作業。 若要建立的作業，您選取的 WCF 用戶端類別，務必**用戶端 （輸出作業）** 選取從**選取合約型別**下拉式清單 （這是預設值）。  
  
3.  在您選取的所有作業，您要為目標，請按一下之後**確定**產生 WCF 用戶端類別。  
  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將兩個檔案加入至您的專案：  
  
-   **OracleDBBindingClient.cs**。 此檔案包含 WCF 用戶端類別和協助程式程式碼產生您所選取的作業。  
  
-   **App.config**。此檔案包含的繫結組態和用戶端端點組態。 這些設定會根據您設定的繫結和連接時，您所選項目[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
    > [!IMPORTANT]
    >  同時使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，如果您未指定類型字串的繫結屬性的值，且其預設值為 null 然後，繫結屬性將不會使用 app.config 檔案中。 您必須以手動方式繫結屬性和其值在 app.config 檔案中，視需要新增。  
  
## <a name="generating-a-wcf-service-contract-by-using-the-add-adapter-service-reference-plug-in"></a>使用產生的 WCF 服務合約加入服務參考外掛程式配接器  
 配接器會公開，讓 Oracle 資料庫，可以將訊息傳送至配接器的用戶端的輸入的作業。 進行此類作業，您必須產生 WCF 服務合約。 例如，配接器會公開輸入的 POLLINGSTMT 作業，以輪詢 Oracle 資料庫。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]執行所指定的查詢**PollingStatement**屬性和 POLLINGSTMT 訊息中使用的應用程式將結果集的傳送繫結。 在此案例中，使用應用程式做為服務和[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]做為用戶端。 您必須，因此，實作 WCF 服務可從配接器接收 POLLINGSTMT 作業。 若要這樣做，您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生.NET 介面代表 POLLINGSTMT 操作的配接器會顯示服務合約。 這個.NET 介面也稱為 WCF 服務合約。 然後，您會實作這個介面可建立 WCF 服務可讓您接收 POLLINGSTMT 作業。  
  
 本節提供有關如何產生 WCF 服務合約使用資訊[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]的輸入配接器所公開的作業。  
  
#### <a name="to-generate-a-wcf-service-contract-for-inbound-operations"></a>若要產生 WCF 服務合約的輸入作業  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]方案總管 中，以滑鼠右鍵按一下您的專案，然後**新增配接器服務參考**。  
  
2.  之後**新增配接器服務參考**對話方塊隨即開啟，請依照下列中的步驟[擷取 Oracle 作業在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)連接到 Oracle 資料庫。 有數個繫結屬性和您可能想要您連接到 Oracle 資料庫的輸入操作時，將 URI 屬性。 例如，針對輸入的輪詢作業 (**POLLINGSTMT**)，您必須指定**PollingStatement**當設定 Oracle 資料庫的連接時，繫結屬性。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]來產生表示 POLLINGSTMT 作業所傳回的結果集的類別會使用這個屬性中指定的 SQL SELECT 陳述式。  
  
3.  您已經連接到 Oracle 資料庫之後，請選取**服務 （輸入操作）** 從**選取合約型別**下拉式清單。  
  
4.  在**選取類別目錄**方塊中，按一下根節點 (**/**)，並瀏覽至您要用來產生服務合約的作業。 例如，輪詢作業中，選取**POLLINGSTMT**從**可用的類別和作業**方塊，然後再按一下**新增**。  
  
5.  若要產生 POLLINGSTMT 作業的 WCF 服務合約，請按一下**確定**。  
  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將三個檔案加入至您的專案：  
  
-   **OracleDBBindingInterface.cs**。 這個檔案包含產生的 WCF 服務合約 （介面），並 POLLINGSTMT 作業的協助程式程式碼。  
  
-   **OracleDBBindingService.cs**。 此檔案包含實作介面 OracleDBBindingInterface.cs 中定義的類別。 您可以實作商務邏輯來處理此類別中的 POLLINGSTMT 方法中，輪詢查詢所傳回的記錄。  
  
-   **App.config**。此檔案包含的繫結組態、 端點行為，以及您所做設定的繫結和連接時的選擇為基礎的服務端點組態[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
    > [!IMPORTANT]
    >  同時使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，如果您未指定類型字串的繫結屬性的值，且其預設值為 null 然後，繫結屬性將不會使用 app.config 檔案中。 您必須以手動方式繫結屬性和其值在 app.config 檔案中，視需要新增。  
  
## <a name="using-svcutilexe-to-generate-a-wcf-client-class-or-a-wcf-service-contract"></a>使用 svcutil.exe 產生 WCF 用戶端類別或 WCF 服務合約  
 您可以使用 svcutil.exe 產生 WCF 用戶端類別或 WCF 服務介面，您的應用程式。 您必須設定要搭配使用 svcutil.exe [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 如需有關設定和使用具有 svcutil.exe [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[Oracle 資料庫與 BizTalk 配接器使用 ServiceModel Metadata Utility Tool](../../adapters-and-accelerators/adapter-oracle-database/use-the-servicemodel-metadata-utility-with-the-oracle-db-adapter-in-biztalk.md)。  
  
 Svcutil.exe 會產生 WCF 用戶端類別或 WCF 服務合約中的輸出檔。 預設檔案名稱是 output.cs。 您必須手動加入這個檔案中的您[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案。  
  
## <a name="see-also"></a>另請參閱  
 [使用 WCF 服務模型開發 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)   
 [使用 WCF 服務模型的 SQL 中執行基本 Insert、 Update、 Delete 和 Select 作業](../../adapters-and-accelerators/adapter-sql/insert-update-delete-or-select-operations-in-sql-using-the-wcf-service-model.md)