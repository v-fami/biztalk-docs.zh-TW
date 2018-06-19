---
title: 如何建構 Web 訊息部分的結構描述型別從 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, Web messages
- Web messages, schema types
- Web messages, creating
- Transform shape [Orchestration Designer]
- Web messages, Transform shape [Orchestration Designer]
ms.assetid: 4452ade6-b10f-4564-bffc-18114896aeeb
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da57e32f2ba4d4d5feb60a6f44cc7d92195852c9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970772"
---
# <a name="how-to-construct-a-web-message-part-from-a-schema-type"></a>如何從結構描述類型建構 Web 訊息部分
從結構描述類型建立 Web 訊息部分使用**轉換**圖形。 或者，您也可以使用 .NET Helper 類別來設定部分，以從結構描述類型建立 Web 訊息部分。 如需有關使用.NET 類別建立訊息類型的詳細資訊，請參閱[使用者程式碼中的 建構訊息](../core/constructing-messages-in-user-code.md)。  
  
### <a name="to-construct-a-web-message-part-from-a-schema-type"></a>若要從結構描述類型建構 Web 訊息部分  
  
1.  新增對應。 如需建立對應資訊，請參閱[如何建立新的對應](../core/how-to-create-new-maps.md)。  
  
2.  在 BizTalk 對應工具中，按一下 **開啟目的結構描述**中**目的結構描述**窗格中的對應，然後在**BizTalk 型別選擇器**對話方塊方塊中，展開  **結構描述** 節點，選取 加入 Web 參考的結構描述，然後按一下**確定**。  
  
    > [!NOTE]
    >  Web 參考結構描述的格式是**\<專案預設命名空間\>。\<Web 參考名稱\>。參考**。  
  
3.  在**目標結構描述的根節點**對話方塊中，選取 目的結構描述的根節點，然後按一下**確定**。 如需如何判斷 Web 訊息部分類型的根節點的詳細資訊，請參閱[如何判斷 Web 訊息部分類型](../core/how-to-determine-a-web-message-part-type.md)。  
  
4.  按一下**開啟來源結構描述**中**來源結構描述**窗格中的對應，然後在**BizTalk 型別選擇器**對話方塊方塊中，展開 **結構描述**節點、 選取要對應資料，來源結構描述，然後按一下**確定**。  
  
5.  在 [BizTalk 對應工具] 中，建立來源結構描述和目標結構描述之間的連結。  
  
6.  開啟現有的協調流程 （或建立新的協調流程），開啟**工具箱**，然後按一下**BizTalk 協調流程** 索引標籤。  
  
7.  拖曳**建構訊息**圖形至協調流程。  
  
8.  編輯**建構訊息**yo 建立 Web 訊息類型的屬性設定為包含訊息執行個體。  
  
9. 拖曳**轉換**圖形拖曳到**建構訊息**圖形，然後按兩下以開啟**轉換組態** 對話方塊。  
  
10. 按一下**現有對應**按鈕，然後選取您在步驟一中建立的對應**完整格式對應名稱**清單方塊。  
  
11. 在**轉換**窗格中，選取**來源**。 在**來源轉換**窗格中，選取有效的訊息執行個體從清單方塊。  
  
12. 在**轉換**窗格中，選取**目的地**。 在**目的轉換**窗格中，選取 Web 訊息執行個體從清單方塊中，然後按一下 **確定**。  
  
 如需有關使用**轉換組態**對話方塊中，請參閱[如何設定 「 轉換 」 圖形](../core/how-to-configure-the-transform-shape.md)。  
  
 您也可以使用這個程序，將 Web 方法回應訊息執行個體對應到其他 Web 訊息執行個體。  
  
## <a name="see-also"></a>請參閱  
 [建構 Web 訊息](../core/constructing-web-messages.md)