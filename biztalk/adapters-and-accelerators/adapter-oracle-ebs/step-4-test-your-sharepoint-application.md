---
title: 步驟 4： 測試 SharePoint 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a859044e-a28e-477e-a20b-f9bb3c9f7405
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 427235d27e4e783111ccdb60f799c228737cd008
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22218238"
---
# <a name="step-4-test-your-sharepoint-application"></a>步驟 4： 測試 SharePoint 應用程式
![步驟 4 之 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：** 您 SharePoint 網站中加入 Web 組件並建立應用程式，您必須測試應用程式擷取 Oracle E-business Suite 中的一些資料之後。 本主題說明如何使用應用程式來擷取 Oracle E-business Suite 中的資料。  
  
## <a name="prerequisites"></a>必要條件  
 您應該建立包含適當的 Web 組件，來擷取商務資料 Web 組件頁面。 請參閱[步驟 3： 建立 SharePoint 應用程式來擷取 Oracle E-business Suite 中的資料](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md)。  
  
### <a name="scenario-1-to-test-the-sharepoint-application-created-using-business-data-list-web-part"></a>案例 1： 測試 SharePoint 應用程式，建立使用商務資料清單網頁組件  
  
1.  啟動 SharePoint 3.0 管理中心。 按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.  
  
2.  在左側瀏覽窗格中，按一下您要在其建立應用程式的 SSP 的名稱。  
  
3.  在左窗格中，按一下 **檢視所有網站內容**。 在右窗格中，按一下 **表單範本**。  
  
4.  在**表單類別**清單中，按一下**MS_SAMPLE_EMPLOYEE**。 當您建立 Web 組件頁面中的，指定這個名稱[案例 1： 使用商務資料清單網頁組件顯示資料](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md)。  
  
5.  搜尋的搜尋字串為基礎的員工。 例如，若要搜尋的所有員工，輸入 **%** 在文字方塊中，按一下**抓取資料**。 下圖顯示從 Oracle E-business Suite 擷取的記錄：  
  
     ![搜尋結果](../../adapters-and-accelerators/adapter-oracle-ebs/media/bdc-result.gif "BDC_Result")  
  
6.  您也可以輸入他們的名字或姓氏來搜尋特定的員工：  
  
    -   使用名字的搜尋，輸入 員工名稱後面接著字母 **%** 符號來傳回符合搜尋準則的所有員工的記錄。  
  
    -   若要搜尋使用的最後一個名稱，請輸入 **%** 後面接著員工的姓氏。  
  
    > [!NOTE]
    >  搜尋字串會區分大小寫。  
  
     ![依員工名字搜尋](../../adapters-and-accelerators/adapter-oracle-ebs/media/b5044c4d-31ec-46d8-b02c-3b26bfe8178e.gif "b5044c4d-31ec-46d8-b02c-3b26bfe8178e")  
  
### <a name="scenario-2-to-test-the-sharepoint-application-created-to-perform-a-full-text-search"></a>案例 2： 測試 SharePoint 應用程式，建立要執行全文檢索搜尋  
  
1.  啟動 SharePoint 3.0 管理中心。 按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.  
  
2.  在左側瀏覽窗格中，按一下您要在其建立應用程式的 SSP 的名稱。  
  
3.  在左窗格中，按一下 **檢視所有網站內容**。 在右窗格中，按一下 **表單範本**。  
  
4.  在**表單類別**清單中，按一下**MS_SAMPLE_EMPLOYEE_Search**。 當您建立 Web 組件頁面中的，指定這個名稱[案例 2： 使用搜尋方塊 」 Web 組件執行搜尋](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-2-search-using-the-search-box-web-part.md)中[案例 2： 使用搜尋方塊 」 Web 組件執行搜尋](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-2-search-using-the-search-box-web-part.md)。  
  
5.  MS_SAMPLE_EMPLOYEE_Search 頁面會顯示您要執行全文檢索搜尋 MS_SAMPLE 員工資料表的 [搜尋] 方塊。 例如，如果您想要搜尋所有位於紐約的員工，輸入`New York`在搜尋方塊中，然後按 ENTER 鍵。  
  
     ![指定搜尋參數](../../adapters-and-accelerators/adapter-oracle-ebs/media/34-search-result.gif "34_Search_Result")  
  
6.  搜尋的結果會顯示頁面。 每個相符的記錄會顯示為搜尋結果頁面中的連結。  
  
     ![搜尋結果](../../adapters-and-accelerators/adapter-oracle-ebs/media/05cc6fdc-8c9f-4312-8579-ef1753d02c63.gif "05cc6fdc-8c9f-4312-8579-ef1753d02c63")  
  
7.  按一下要檢視個別的員工記錄的搜尋結果中的連結。  
  
     ![詳細的員工記錄](../../adapters-and-accelerators/adapter-oracle-ebs/media/36-search-result2.gif "36_Search_Result2")  
  
## <a name="summary"></a>摘要  
 在本教學課程中，您可以建立您想要從 SharePoint 入口網站存取 Oracle E-business Suite 成品的 WCF 服務。 您也會建立 Oracle E-business Suite 成品的應用程式定義匯入 SharePoint 入口網站來建立及搜尋 Oracle E-business Suite 中的資料呈現的 Web 組件。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程： 從 SharePoint 網站上的 Oracle E-business Suite 中呈現的資料](../../adapters-and-accelerators/adapter-oracle-ebs/tutorial-present-data-from-oracle-e-business-suite-on-a-sharepoint-site.md)