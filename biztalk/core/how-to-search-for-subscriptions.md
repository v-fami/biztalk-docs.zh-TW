---
title: 如何搜尋訂用帳戶 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Query tab [Administration Console], subscriptions
- Query tab [Administration Console], searching
- subscriptions, viewing
- subscriptions, searching
ms.assetid: 95f8fd20-2750-412b-a67b-18976e7706e2
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07230ace1e097d71e728110b8f2280e903ea67b8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023244"
---
# <a name="how-to-search-for-subscriptions"></a>如何搜尋訂閱
您可以使用**查詢**在 BizTalk Server 管理主控台，來搜尋訂用帳戶 索引標籤。 當您要檢視系統中所定義的所有訂閱時，這非常有用。 在疑難排解路由失敗時，您可以檢視訂閱以查看是否有任何訂閱設定不當，因此導致路由失敗。  

## <a name="prerequisites"></a>必要條件  
 若要執行此程序，您必須以「BizTalk Server 操作員」群組的成員身分登入。  

### <a name="to-search-for-subscriptions"></a>搜尋訂閱  

1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。  

2. 在主控台樹狀目錄中展開 [[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]]，然後按一下 BizTalk 群組。  

3. 在 詳細資料 窗格中，按一下**新的查詢** 索引標籤。  

4. 在 **查詢運算式**群組中**值**欄中，選取**訂用帳戶**從下拉式清單方塊。  

5. 在 **欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (* *\\* * *)，選取一或多個項目：  


   |          項目           |                                    描述                                    |
   |-------------------------|-----------------------------------------------------------------------------------|
   |   **最大相符項目**   |                         要顯示的相符記錄數目。                         |
   | **服務執行個體識別碼** |               您可以依據服務執行個體識別碼篩選訂閱。                |
   |    **服務名稱**     |                   您可以依據服務名稱篩選訂閱。                   |
   |  **訂閱類型**  | 您可以依據「啟動訂閱」或「執行個體訂閱」篩選訂閱。 |


6. 完成**值**適當選取您在中所做的資料行**欄位名**資料行。  

7. 繼續新增其他行至視需要查詢中，藉由完成**欄位名**，**運算子**，和**值**資料行，然後再按一下**執行查詢**。  

## <a name="see-also"></a>另請參閱  
 [使用管理主控台查詢索引標籤](../core/using-the-administration-console-query-tab.md)