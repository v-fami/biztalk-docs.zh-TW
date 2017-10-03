---
title: "步驟 4： 測試您的 SharePoint Application1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7ded5a5-88d5-40aa-814b-70bc0a7dcfa3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b8be51df02bd9796b41201c0495758c281e8f14
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-test-your-sharepoint-application"></a>步驟 4： 測試 SharePoint 應用程式
![步驟 4 之 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：**您 SharePoint 網站中加入 Web 組件，並建立應用程式，您必須測試應用程式擷取從 SAP 系統的一些資料之後。 本主題說明如何使用應用程式從 SAP 系統中擷取資料。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您應該建立包含適當的 Web 組件，來擷取商務資料 Web 組件頁面。 請參閱[步驟 3： 建立 SharePoint 應用程式來擷取資料，從 SAP](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md)。  
  
### <a name="to-test-the-sharepoint-application"></a>若要測試 SharePoint 應用程式  
  
1.  啟動 SharePoint 3.0 管理中心。 按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.  
  
2.  在左側瀏覽窗格中，按一下您要在其建立應用程式的 SSP 的名稱。  
  
3.  在左窗格中，按一下 **檢視所有網站內容**。 在右窗格中，按一下 **表單範本**。  
  
4.  在**表單類別**清單中，按一下**Customer_SalesOrders**。 當您建立 Web 組件頁面時，您可以指定此名稱。 下圖顯示您所建立的 Web 組件頁面。  
  
     ![已完成的 Web 組件頁面](../../adapters-and-accelerators/adapter-sap/media/3e9f22b1-8285-40f4-a67d-b51173c93671.gif "3e9f22b1-8285-40f4-a67d-b51173c93671")  
  
5.  搜尋的搜尋字串為基礎的客戶。 例如，搜尋客戶名稱開頭為"John E"。 若要這樣做：  
  
    1.  在 客戶清單區段中，從第一個清單中，按一下**CustomerName**。  
  
    2.  從第二個清單中，按一下**開頭**。  
  
    3.  在文字方塊中，輸入**John E**。  
  
    4.  按一下**抓取資料**連結，或按 ENTER。 下圖顯示符合搜尋條件的記錄從 SAP 系統擷取。  
  
         ![搜尋 SAP 系統從結果](../../adapters-and-accelerators/adapter-sap/media/c97e9e2c-0908-46af-9a54-8a4354847c47.gif "c97e9e2c-0908-46af-9a54-8a4354847c47")  
  
6.  您現在可以看到在清單中的任何客戶的詳細資料與銷售訂單的客戶，如果有的話。 若要這樣做，請按一下 [針對客戶編號] 選項按鈕。 頁面重新整理呈現和個別的 Web 組件中的特定客戶的銷售訂單的詳細資料。  
  
     ![在 SharePoint 上顯示的 SAP 資料](../../adapters-and-accelerators/adapter-sap/media/29fc4a9e-facd-4455-bcfe-5f4d866b2dc7.gif "29fc4a9e-facd-4455-bcfe-5f4d866b2dc7")  
  
     如果已正確地顯示客戶及相關聯的銷售訂單的詳細資訊，您已順利完成本教學課程。 如果沒有或不正確的資料會顯示，請仔細檢查您的工作，並確定您正確地執行所有工作。  
  
## <a name="summary"></a>摘要  
 在本教學課程，您會建立您想要從 SharePoint 入口網站存取 SAP 成品的 WCF 服務。 您也會建立 SAP 成品的應用程式定義匯入 SharePoint 入口網站來建立 Web 組件來呈現資料的 SAP 系統。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 1： 從 SharePoint 網站上的 SAP 系統中呈現資料](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)