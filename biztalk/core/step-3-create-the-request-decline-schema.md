---
title: 步驟 3： 建立拒絕要求結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1ce166c-1be1-4ef4-9d00-3da7038d4ada
caps.latest.revision: 39
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ff343c58e836bc0738f0200016308eb7a4d90b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278550"
---
# <a name="step-3-create-the-request-decline-schema"></a>步驟 3：建立拒絕要求結構描述
![步驟 5 的 3](../core/media/step-3of5.gif "Step_3of5")  
  
 **若要完成的時間：** 7 分鐘  
  
 **目標：** 在此步驟中，您會建立訊息的結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]傳送傳回倉儲的商務程序拒絕庫存補充要求的情況。  
  
 **用途：** 結構描述會定義資料的要求拒絕訊息結構。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用結構描述來識別及訊息中的資料互動。  
  
## <a name="prerequisites"></a>必要條件  
 開始此步驟之前，請注意下列需求：  
  
-   在開始此步驟之前必須先完成[步驟 1： 建立 EAISchemas 專案](../core/step-1-create-eaischemas-project.md)。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-create-the-request-decline-schema"></a>建立拒絕要求結構描述  
  
1.  在 方案總管 中，以滑鼠右鍵按一下**EAISchemas**專案，指向**新增**，然後按一下 **新項目**。  
  
2.  在**加入新項目-EAISchemas**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**已安裝的範本**|按一下**結構描述檔案**，然後按一下 **結構描述**。|  
    |**名稱**|輸入 `RequestDecline.xsd`。|  
  
3.  按一下 **[加入]**。  
  
4.  在 [BizTalk 編輯器] 中，從結構描述樹狀目錄中，按一下**根**節點以選取它。  
  
5.  在 [屬性] 窗格中，將值變更**節點名稱**屬性`DeclineReq`，然後按 ENTER 鍵。  
  
6.  在結構描述樹狀目錄中，以滑鼠右鍵按一下**declinereq**節點，指向**插入結構描述節點**，然後按一下 **子欄位項目**。  
  
7.  型別`ReqID`做為項目，並再按 ENTER 鍵的新名稱。  
  
8.  加入名為第二個子欄位項目`GrandTotal`。  
  
9. 按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您已經針對商務程序拒絕庫存要求的情況，為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳回倉儲的訊息建立結構描述。  
  
## <a name="next-steps"></a>後續步驟  
 藉由重新格式化要求訊息的方式，建立協調流程所需的對應來建立要求拒絕訊息。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 1： 建立 EAISchemas 專案](../core/step-1-create-eaischemas-project.md)  
 [步驟 2： 建立庫存要求結構描述](../core/step-2-create-the-inventory-request-schema.md)   
 [步驟 4： 建立地圖](../core/step-4-create-the-map.md)   
 [步驟 5： 建置 Eaischema 專案](../core/step-5-build-the-eaischemas-project.md)   
 [使用 BizTalk 編輯器建立結構描述](../core/creating-schemas-using-biztalk-editor.md)