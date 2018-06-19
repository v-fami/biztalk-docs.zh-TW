---
title: 產生 WCF 用戶端或 Oracle E-business Suite 方案成品的 WCF 服務合約 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c7ffd857-a177-423a-ae83-685d11b7aec6
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc7fb7dc0df1c2cbf4c4f8b1118cba07df6c7231
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217462"
---
# <a name="generate-a-wcf-client-or-a-wcf-service-contract-for-oracle-e-business-suite-solution-artifacts"></a>產生 WCF 用戶端或 Oracle E-business Suite 方案成品的 WCF 服務合約
您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別或 WCF 服務合約 （介面） 為目標的 Oracle E-business Suite 成品中選取的作業。 您也可以使用 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別或 WCF 服務合約。不過，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]公開 ServiceModel Metadata Utility Tool，透過標準的 Microsoft Windows 介面的功能。 它也提供不是使用 svcutil.exe 工具，可用的瀏覽和搜尋功能，並在產生組態檔，根據您選取當您連接到 Oracle E-business Suite 繫結屬性。  
  
## <a name="generating-a-client-class-by-using-the-add-adapter-service-reference-plug-in"></a>使用產生的用戶端類別新增配接器服務參考外掛程式  
 執行下列步驟來產生 WCF 用戶端類別使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-generate-a-wcf-client-class"></a>若要產生 WCF 用戶端類別  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]方案總管 中，以滑鼠右鍵按一下您的專案，然後**新增配接器服務參考**。  
  
2.  之後**新增配接器服務參考**對話方塊隨即開啟，請依照下列中的步驟[擷取 Oracle E-business Suite 作業在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)連接到 Oracle E-business Suite 和瀏覽和搜尋作業。 若要建立的作業，您選取的 WCF 用戶端類別，務必**用戶端 （輸出作業）** 選取從**選取合約型別**下拉式清單 （這是預設值）。  
  
3.  在您選取的所有作業，您要為目標，請按一下之後**確定**產生 WCF 用戶端類別。  
  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將兩個檔案加入至您的專案：  
  
-   **OracleEBSBindingClient.cs**。 此檔案包含 WCF 用戶端類別和協助程式程式碼產生您所選取的作業。  
  
-   **app.config**。此檔案包含的繫結組態和用戶端端點組態。 這些設定會根據您設定的繫結和連接時，您所選項目[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
    > [!IMPORTANT]
    >  同時使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，如果您未指定類型字串的繫結屬性的值，且其預設值為 null 然後，繫結屬性將不會使用 app.config 檔案中。 您必須以手動方式繫結屬性和其值在 app.config 檔案中，視需要新增。  
  
## <a name="generating-a-wcf-service-contract-by-using-the-add-adapter-service-reference-plug-in"></a>使用產生的 WCF 服務合約加入服務參考外掛程式配接器  
 配接器會公開啟用 Oracle E-business Suite，將訊息傳送至配接器用戶端的輸入的作業。 進行此類作業，您必須產生 WCF 服務合約。 本節提供有關如何產生服務合約的輸入配接器所公開的作業的資訊。  
  
 執行下列步驟來產生 WCF 服務合約使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-generate-a-wcf-service-contract-for-inbound-operations"></a>若要產生 WCF 服務合約的輸入作業  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]方案總管 中，以滑鼠右鍵按一下您的專案，然後**新增配接器服務參考**。  
  
2.  之後**新增配接器服務參考**對話方塊隨即開啟，請依照下列中的步驟[擷取 Oracle E-business Suite 作業在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)來連接到 Oracle E-business Suite 的資訊。 有數個繫結屬性和您可能想要您連接到 Oracle E-business Suite 的資訊時，將 URI 屬性。  
  
3.  您已經連接到 Oracle E-business Suite 的資訊之後，請選取**服務 （輸入操作）** 從**選取合約型別**下拉式清單。  
  
4.  在**選取類別目錄**方塊中，瀏覽至 輸入您要產生服務合約的作業。 例如，對於**通知**作業中，按一下根節點 (**/**)，請選取**通知**從**可用的類別和作業**方塊，然後再按一下**新增**。 如需有關如何瀏覽的輸入操作的指示，請參閱[瀏覽、 搜尋及擷取 Oracle E-business Suite 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)。  
  
5.  若要產生 WCF 服務合約的作業，請按一下**確定**。  
  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將三個檔案加入至您的專案：  
  
-   **OracleEBSBindingInterface.cs**。 這個檔案包含產生的 WCF 服務合約 （介面），並輸入作業的協助程式程式碼。  
  
-   **OracleEBSBindingService.cs**。 此檔案包含實作介面 OracleDBBindingInterface.cs 中定義的類別。 您可以實作商務邏輯來處理輸入作業所傳回的記錄。  
  
-   **app.config**。此檔案包含的繫結組態、 端點行為，以及您所做設定的繫結和連接時的選擇為基礎的服務端點組態[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
    > [!IMPORTANT]
    >  同時使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，如果您未指定類型字串的繫結屬性的值，且其預設值為 null 然後，繫結屬性將不會使用 app.config 檔案中。 您必須以手動方式繫結屬性和其值在 app.config 檔案中，視需要新增。  
  
## <a name="using-svcutilexe-to-generate-a-wcf-client-class-or-a-wcf-service-contract"></a>使用 svcutil.exe 產生 WCF 用戶端類別或 WCF 服務合約  
 您可以使用 svcutil.exe 產生 WCF 用戶端類別或 WCF 服務介面，您的應用程式。 您必須設定要搭配使用 svcutil.exe [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  
  
 Svcutil.exe 會產生 WCF 用戶端類別或 WCF 服務合約中的輸出檔。 預設檔案名稱是 output.cs。 您必須手動加入這個檔案中的您[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案。 如需 svcutil.exe 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=139432](http://go.microsoft.com/fwlink/?LinkId=139432)。