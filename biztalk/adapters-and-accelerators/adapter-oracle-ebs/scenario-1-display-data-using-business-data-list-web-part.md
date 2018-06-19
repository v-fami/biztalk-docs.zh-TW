---
title: 案例 1： 使用商務資料清單網頁組件的資料顯示。 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3831814-8b70-4352-b22f-cebd08750ef5
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1add974ca3ad0b80b7838b120920f4de47f1650
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217430"
---
# <a name="scenario-1-display-data-using-business-data-list-web-part"></a>案例 1： 使用商務資料清單網頁組件的顯示資料
我們將使用**商務資料清單**Web 組件**Finder**方法執行個體。 此 Web 組件可讓您指定搜尋運算式來擷取 Oracle E-business Suite 中的員工清單。 此教學課程中，這稱為顯示員工 Web 組件。 本節提供指示來建立此 Web 組件。 如需建立 Web 組件的詳細資訊，請參閱 < 自訂商務資料清單、 Web 組件和站台 」 在[http://go.microsoft.com/fwlink/?LinkId=104131](http://go.microsoft.com/fwlink/?LinkId=104131)。  
  
 加入 Web 組件之前，您必須建立 Web 組件頁面。  
  
## <a name="creating-a-web-part-page"></a>建立網頁組件  
 本節提供建立 Web 組件頁面的指示。  
  
###  <a name="WebPart"></a>若要建立 Web 組件頁面  
  
1.  啟動 SharePoint 3.0 管理中心。 按一下**啟動**，指向**所有程式**，指向 [ **Microsoft Office Server**，然後按一下**SharePoint 3.0 管理中心]**。  
  
2.  在左側瀏覽窗格中，按一下您要匯入應用程式定義的 SSP 的名稱。  
  
3.  在右上角的 共用服務管理 頁面上，按一下 **網站動作**，然後按一下 **建立**。  
  
     ![若要建立的 web 組件的功能表](../../adapters-and-accelerators/adapter-oracle-ebs/media/a9872c3e-f823-4c47-a538-19242565d2e9.gif "a9872c3e-f823-4c47-a538-19242565d2e9")  
  
4.  在 [建立] 頁面中**網頁**區段中，按一下**Web 組件頁面**。  
  
5.  在新的 Web 組件 頁面上，執行下列作業：  
  
    1.  在**名稱**欄位中，輸入頁面的名稱。 此教學課程中，輸入相同的名稱。 **MS_SAMPLE_EMPLOYEE**。  
  
    2.  選取**檔案已經存在覆寫**核取方塊，如果您想要覆寫舊的頁面，與您建立新的頁面名稱相同。  
  
    3.  在**配置**] 區段中，從**選擇版面配置範本**方塊中，選取 [Web 組件頁面的版面配置。 此教學課程中，選取**整頁、 垂直**。  
  
    4.  在**儲存位置**區段的**文件庫**清單中，按一下**表單範本**。  
  
    5.  按一下 **[建立]**。 在建立後下, 圖顯示 Web 組件頁面。  
  
         ![新的 WebPart 頁面](../../adapters-and-accelerators/adapter-oracle-ebs/media/23-web-part.gif "23_Web_Part")  
  
    6.  您現在必須將 Web 組件加入此頁面。  
  
## <a name="adding-a-business-data-list-web-part"></a>新增商務資料清單網頁組件  
 您現在必須新增 Web 組件頁面的商務資料清單網頁組件。 使用此 Web 組件會擷取員工記錄的清單，從 MS_SAMPLE_EMPLOYEE 介面資料表中符合搜尋運算式的 Oracle E-business Suite。 此 Web 組件會對應至**Finder**方法執行個體 (*Finder_Instance*) 建立的商務資料目錄定義編輯器。  
  
#### <a name="to-add-a-business-data-list-web-part"></a>若要加入商務資料清單網頁組件  
  
1.  在 MS_SAMPLE_EMPLOYEE] 頁面上，按一下 [**新增網頁組件**。  
  
2.  在**新增網頁組件**對話方塊中，於**商務資料**區段中，選取**商務資料清單**核取方塊，然後**新增**。  
  
     ![若要建立商務資料 Web 組件的選項](../../adapters-and-accelerators/adapter-oracle-ebs/media/ae7c952c-1592-495f-9452-c1bffd44421c.gif "ae7c952c-1592-495f-9452-c1bffd44421c")  
  
3.  新增商務資料清單 Web 組件中，按一下 **開啟工具窗格**連結。  
  
     ![Web 組件中開啟工具窗格](../../adapters-and-accelerators/adapter-oracle-ebs/media/4e7a1cb1-69dc-4e0d-a211-6a217dc4a549.gif "4e7a1cb1-69dc-4e0d-a211-6a217dc4a549")  
  
4.  在右窗格中，開啟 [商務資料清單] 工具窗格。 在**商務資料清單** 區段中，針對**類型**欄位中，按一下**瀏覽** 按鈕。  
  
     ![商務資料清單 工具窗格](../../adapters-and-accelerators/adapter-oracle-ebs/media/24-bdc-browse.gif "24_BDC_Browse")  
  
5.  在**商務資料型別選擇器**對話方塊中，選取**MS_SAMPLE_EMPLOYEE_Instance**應用程式，，然後按一下**確定**。  
  
     ![選取的應用程式執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/25-bdc-picker.gif "25_BDC_Picker")  
  
6.  展開**外觀** 節點，然後在**標題**方塊中，輸入 Web 組件的標題。 此 Web 組件中，輸入**員工清單**。  
  
7.  在 商務資料清單 工具窗格中，按一下 **套用**，然後按一下 **確定**。 商務資料清單網頁組件現在看起來如下所示：  
  
     ![商務資料清單 」 Web 組件](../../adapters-and-accelerators/adapter-oracle-ebs/media/26-bdc-webpart.gif "26_BDC_WebPart")  
  
8.  Web 組件會列出執行 MS_SAMPLE_EMPLOYEE 介面資料表的 Select 作業所傳回的欄位。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3： 建立 SharePoint 應用程式來擷取 Oracle E-business Suite 中的資料](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md)   
 [使用搜尋方塊 」 Web 組件搜尋案例 2:](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-2-search-using-the-search-box-web-part.md)