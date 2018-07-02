---
title: 如何搜尋受到追蹤的服務執行個體 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b6337df9-8c2e-4d4a-a64b-cc040f83bd91
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3770e871e7be022ff7f4597b8d3eb4d8f307cc37
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966511"
---
# <a name="how-to-search-for-tracked-service-instances"></a>如何搜尋受到追蹤的服務執行個體
您可以使用**查詢**索引標籤中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來搜尋所有追蹤的服務執行個體。 若要尋找服務執行個體，您可以根據組件的名稱與版本、執行個體存留期的開始與結束時間、服務類別的名稱或執行個體識別碼、主控件名稱、錯誤碼以及服務執行個體的狀態，來進行搜尋。  

## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 操作員」群組成員的身分來登入，才能執行此程序。  

### <a name="to-search-for-tracked-service-instances"></a>若要搜尋受到追蹤的服務執行個體  

1. 按一下 **開始**，按一下**程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。  

2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，然後按一下 BizTalk 群組。  

3. 在 詳細資料 窗格中，按一下**新的查詢** 索引標籤。  

4. 在 **查詢運算式**群組中**值**欄中，選取**追蹤服務執行個體**從下拉式清單方塊。  

5. 在 **欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (* *\\* * *)，選取一或多個項目：  


   |          項目           |                     描述                      |
   |-------------------------|------------------------------------------------------|
   |    **組件名稱**    |    服務執行個體的組件名稱。    |
   |  **組件版本**   |           服務執行個體的 版本。           |
   |      **結束時間**       |          服務執行個體的 結束時間。           |
   |     **錯誤碼**      | 任何 與服務執行個體相關聯的錯誤碼。 |
   |      **Host Name**      |        服務執行個體的 主控件名稱。        |
   |   **最大相符項目**   |          要顯示的相符記錄數目。           |
   |    **服務類別**    |          服務執行個體的 類別。          |
   | **服務執行個體識別碼** |               服務執行個體識別碼。               |
   |    **服務名稱**     |          服務執行個體的名稱。           |
   |     **Start Time**      |       服務執行個體的開始時間。        |
   |        **State**        |          服務執行個體的狀態。          |


6. 完成**值**適當選取您在中所做的資料行**欄位名**資料行。  

7. 繼續新增其他行至適當的查詢中，藉由完成**欄位名**，**運算子**，並**值**資料行，然後再按一下**執行查詢**。  

## <a name="see-also"></a>另請參閱  
 [使用管理主控台查詢索引標籤](../core/using-the-administration-console-query-tab.md)