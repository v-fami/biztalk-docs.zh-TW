---
title: 如何在活動搜尋中建立查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Query Builder [BAM portal], creating queries
- queries [BAM], saving
- queries [BAM], creating
- queries [BAM], executing
- Query Builder [BAM portal], executing queries
- Query Builder [BAM portal], opening queries
- Query Builder [BAM portal], saving queries
- queries [BAM], opening
ms.assetid: 7940e47d-10e4-4eb1-b4e6-a8b98461e3a8
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3fd89ec71319a70c0330ebef80c7c8165cacf6c2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989743"
---
# <a name="how-to-create-a-query-in-activity-search"></a>如何在活動搜尋中建立查詢
商務使用者與其他需要接收商務事件和狀態等相關通知的使用者，可以使用查詢建立活動搜尋，然後據以發出警示。  
  
## <a name="prerequisites"></a>必要條件  
 您必須具備部署檢視。  
  
### <a name="to-open-a-query"></a>若要開啟查詢  
  
1. 按一下 **開始**，指向**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BAM 入口網站**。  
  
2. 在 **我的檢視**框架的入口網站中，按一下 現有的檢視，以展開該檢視所提供的功能表。  
  
3. 按一下 **活動搜尋**，展開檢視可用的活動清單。  
  
4. 按一下清單中的活動， 這樣會載入所選取活動的 [活動搜尋] 頁面。  
  
5. 在內容框架中，頂端的頁面上，按一下**瀏覽** 按鈕以開啟**選擇檔案** 對話方塊。  
  
6. 瀏覽至您先前儲存查詢的資料夾。  
  
7. 按一下儲存的查詢。  
  
8. 按一下 [**開啟**] 按鈕。 這樣會載入在左邊的文字方塊中查詢的路徑**瀏覽** 按鈕。 您也可以直接在文字方塊中輸入查詢的路徑。  
  
9. 按一下 [**開啟查詢**右邊的按鈕**瀏覽**] 按鈕。  
  
### <a name="to-construct-a-query"></a>建構查詢  
  
1. 按一下 **開始**，指向**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BAM 入口網站**。  
  
2. 在 **我的檢視**入口網站的清單目前沒有框架設定檢視。 每個檢視底下都會列出三項可以在檢視上執行的工作。 如果檢視目前為摺疊狀態，按一下檢視即可展開工作清單。  
  
3. 按一下 **活動搜尋**，展開檢視可用的活動清單。  
  
4. 按一下清單中的活動， 這樣會載入所選取活動的 [活動搜尋] 頁面。  
  
5. 在內容框架中，在**查詢**方塊中，選擇從欄位**商務資料**下拉式清單，用於在查詢中的比較。  
  
6. 從**運算子**下拉式清單中，選取要使用的比較運算子。  
  
7. 在 **值**方塊中，輸入要比較的值。 您只能輸入可用於比較欄位的適當值 (如果商務資料項目是日期欄位，則比較資料即是適用於您的文化特性設定格式的日期或日期時間)。  
  
8. 如果您有更多子句來加入至查詢時，按一下**新增**查詢方塊右邊的按鈕。 這樣會為下一個子句新增新的一行。 您可以選擇是否要使用 AND 或 OR 以聯結子句。  
  
   > [!NOTE]
   >  您無法將子句分組成更複雜的查詢。 查詢是由 AND 或 OR 運算子聯結而成的一組簡單子句。  
  
   > [!NOTE]
   >  如果您在這些程序期間按 上一頁 按鈕，並收到 「 警告： 頁面已經過期，「 您可以按 F5 來取回原來的內容。 您可能必須按數次 F5。  
  
9. 在資料行選擇器選取資料或從里程碑**可用的資料和里程碑**查詢以傳回做為資料的清單方塊。 您可以按住 SHIFT 鍵，再按一下所要傳回之群組的第一個和最後一個項目，以選取多個項目。 您也可以按住 CTRL 鍵，再一一選取清單中要傳回的項目，以選取多個項目。  
  
10. 使用**>>** 按鈕以移至選取的項目**項目可顯示**清單方塊。 您可以從這份清單移除項目，藉由選取並使用**<<** 按鈕，移回資料和里程碑清單方塊。  
  
11. 選取查詢要傳回的所有項目之後，您可以重新排列結果，以決定各欄位的顯示順序。 若要將資料行移至所傳回的資料集中的第一個位置中，選取該按一下它，然後按一下**下移**按鈕，直到它位於最上層的項目清單。 同樣地，若要移動項目中傳回的資料集的更新位置，選取的項目按一下它，然後按一下**下移**按鈕，直到它是在您要它顯示的位置。  
  
### <a name="to-save-a-query"></a>若要儲存查詢  
  
1.  在內容框架中，頂端的頁面上，按一下**另存查詢** 按鈕以開啟**儲存檔案** 對話方塊。  
  
2.  在 **檔案下載** 對話方塊中，按一下**儲存** 按鈕。  
  
3.  瀏覽至您要儲存查詢的位置。  
  
4.  您可以接受查詢提供的預設名稱，或者您可以輸入新的名稱，在**檔案名**文字方塊。  
  
5.  按一下 [**儲存**] 按鈕。  
  
### <a name="to-execute-a-query"></a>若要執行查詢  
  
1. 按一下 **開始**，指向**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BAM 入口網站**。  
  
2. 在 **我的檢視**框架的入口網站中，按一下 現有的檢視，以展開該檢視所提供的功能表。  
  
3. 按一下 **活動搜尋**，展開檢視可用的活動清單。  
  
4. 按一下清單中的活動， 這樣會載入所選取活動的 [活動搜尋] 頁面。  
  
5. 開啟現有的查詢，或建立新的查詢。  
  
6. 在入口網站的內容框架中，按一下**執行查詢** 按鈕。  
  
## <a name="see-also"></a>另請參閱  
 [BAM 入口網站中的活動搜尋](../core/activity-searches-in-the-bam-portal.md)