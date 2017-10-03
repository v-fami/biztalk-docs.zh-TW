---
title: "步驟 4： 測試 SharePoint 應用程式使用 Siebel 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec1392fa-fdc1-42be-b4dc-75a55d8fa400
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85cebcafcdf768686ed3f7382a0838db5062d96b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-test-your-sharepoint-application-with-the-siebel-adapter"></a>步驟 4： 測試 SharePoint 應用程式使用 Siebel 配接器
![步驟 4 之 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")  
  
 **若要完成的時間：** 5 分鐘。  
  
 **目標：**您 SharePoint 網站中加入 Web 組件，並建立應用程式，您必須測試應用程式擷取來自 Siebel 系統的一些資料之後。 本節提供有關如何使用來自 Siebel 系統擷取資料的應用程式的指示。  
  
## <a name="prerequisites"></a>必要條件  
 您應該建立包含適當的 Web 組件，來擷取商務資料的 Web 組件頁面。 請參閱[步驟 3： 建立 SharePoint 應用程式資料擷取 Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md)。  
  
### <a name="to-test-the-sharepoint-application"></a>若要測試 SharePoint 應用程式  
  
1.  啟動 SharePoint 3.0 管理中心。 按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.  
  
2.  在左側瀏覽窗格中，按一下您要在其建立應用程式的 SSP 的名稱。  
  
3.  在左窗格中，按一下 **檢視所有網站內容**。 從右窗格中，按一下**表單範本**。  
  
4.  在**表單類別**清單中，按一下**Siebel 帳戶**。 您建立 Web 組件頁面時指定此名稱。 下圖顯示您所建立的 Web 組件頁面。  
  
     ![已完成的 Web 組件頁面](../../adapters-and-accelerators/adapter-siebel/media/a0bfe7af-0246-4f0b-aa0d-0ee084456003.gif "a0bfe7af-0246-4f0b-aa0d-0ee084456003")  
  
5.  查詢搜尋字串為基礎的商務帳戶元件。 例如，指定搜尋運算式`[Name] LIKE ‘W*’`。 若要這樣做：  
  
    1.  在**帳戶清單**區段中的，從第一個清單中，選取**SearchExpression**，然後選取**等於**。  
  
    2.  在文字欄位中，輸入`[Name] LIKE ‘W*’`。  
  
    3.  按一下**抓取資料**連結，或按下 ENTER。 下圖顯示符合搜尋條件的記錄擷取來自 Siebel 系統。  
  
         ![搜尋結果來自 Siebel 系統](../../adapters-and-accelerators/adapter-siebel/media/6c4721ac-c7bc-4626-9ee0-55cf322026cf.gif "6c4721ac-c7bc-4626-9ee0-55cf322026cf")  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 1： 從 SharePoint 網站上的 Siebel 系統中呈現資料](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)