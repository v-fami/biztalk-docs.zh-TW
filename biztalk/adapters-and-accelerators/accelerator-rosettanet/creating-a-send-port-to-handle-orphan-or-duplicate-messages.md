---
title: 建立傳送埠，處理遭遺棄或重複的訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, duplicate messages
- messages, orphaned messages
- send ports, duplicate messages
- send ports, orphaned messages
- messages, send ports
ms.assetid: 61d51206-13e3-4d32-a184-866248db9b45
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc4e6e8650f0da1446a48b5da8c8f7c2142af7bb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997895"
---
# <a name="creating-a-send-port-to-handle-orphan-or-duplicate-messages"></a>建立傳送埠，處理遭遺棄或重複的訊息
本主題說明如何設定傳送埠，讓您可以用來刪除遭遺棄或重複的訊息。  
  
 遭遺棄或重複的訊息可能是個問題如果 Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]公開程序協調流程已完成處理訊息的第一個複本之後，會收到一則訊息的其他複本。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 將這些訊息標示為重複項目，並加以擱置。 您可以在 BizTalk 管理主控台中檢視這些訊息。 如需有關 BizTalk 管理主控台的詳細資訊，請參閱 「 使用 BizTalk 管理主控台 」 中的 BizTalk Server 說明。  
  
 除非您檢閱或刪除這些遭遺棄或重複的訊息，否則它們會持續存在於 BizTalk 管理主控台中。 刪除它們最有效的方式，就是設定具有篩選遭遺棄或重複訊息功能的傳送埠。 您可以移動它們使用 BizTalk Server 中提供的任何運輸方式。 比方說，您可以使用檔案傳輸來移動它們。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 將作為檔案遭遺棄或重複的訊息傳送到硬碟上的位置。 如此便可以輕易將它們刪除。 這個連接埠可以是登錄或停止的狀態，在這種情況下，所有傳送至這個連接埠的訊息都將會在這個傳送埠下方，顯示為遭擱置的狀態。  
  
> [!NOTE]
>  您可以建立特殊的管線元件，從 MessageBox 資料庫刪除這些訊息，而不用建立傳送埠來處理重複/遭遺棄的訊息。 您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] SDK 中的 FixMsg 元件做為範本。 但必須修改 `IComponent.Execute` 方法，才能傳回 null。 這便會導致 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 捨棄任何傳送至含有該元件之管線的訊息。 因此必須要編譯這個管線元件，並將它加入傳送管線，然後再編譯、部署以及選取這個接受埠的傳送管線。 如需詳細資訊，請參閱 「 CustomComponent ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]範例) 」 在 BizTalk Server 說明中。  
  
### <a name="to-create-a-send-port-to-handle-orphan-or-duplicate-messages"></a>建立傳送埠，處理遭遺棄或重複的訊息  
  
1. 在 [[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檢視**功能表上，按一下**BizTalk 總管] 中**。  
  
2. 在 [BizTalk 總管] 中，展開**BizTalk 管理資料庫**，然後展開**傳送連接埠**。  
  
3. 以滑鼠右鍵按一下**傳送埠**，然後按一下**新增傳送埠**。  
  
4. 在 [建立新傳送埠] 視窗中，選取**靜態單向連接埠**，然後按一下**確定**。  
  
5. 在 [靜態單向傳送埠屬性] 視窗中，在**名稱**方塊中，輸入傳送埠的名稱。  
  
6. 在左窗格中，按一下**傳輸**。 在右窗格中，按一下**傳輸類型**，然後選取**檔案**做為傳輸類型。 按一下旁邊的省略符號按鈕 （...）**位址 (URI)**，輸入在您的硬碟上的位置，然後按一下**確定**。  
  
7. 在左窗格中，按一下**傳送**，按一下**傳送管線**，然後選取**Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**。  
  
8. 在左窗格中，按一下**篩選，並將對應**，然後按一下**篩選**。  
  
9. 在右窗格中的第一行上的**屬性**，選取**Microsoft.Solutions.BTARN.GlobalSchemas.IsDuplicateMessage**從下拉式清單中，保留**運算子**作為**==**，輸入 **，則為 True**如**值**，然後選取 **或**從的下拉式清單**群組**。  
  
10. 在右窗格中，在第二行的**屬性**，選取**Microsoft.Solutions.BTARN.GlobalSchemas.IsOrphanMessage**從下拉式清單中，保留**運算子**作為**==**，然後輸入 **，則為 True**如**值**。  
  
11. 按一下 [確定] 。  
  
12. 在 [BizTalk 總管] 中，以滑鼠右鍵按一下傳送埠的名稱，請按一下**登錄**。 傳送埠登錄完成後，以滑鼠右鍵按一下傳送埠，然後**啟動**。  
  
## <a name="see-also"></a>另請參閱  
 [程式設計指南](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)