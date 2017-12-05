---
title: "如何刪除傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [send ports], deleting
- send ports, deleting
- deleting, send ports
ms.assetid: aff5980e-57bf-400c-82bd-3d02e143f227
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63355f742f12fbbaf57ccde7a1406dbb694ee073
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-delete-a-send-port"></a>如何刪除傳送埠
本主題描述如何使用 BizTalk Server 管理主控台，從 BizTalk 應用程式中刪除傳送埠。 這樣做也會從群組的 BizTalk 管理資料庫中刪除傳送埠。  
  
> [!IMPORTANT]
>  移除傳送埠時，與該連接埠關聯的任何執行中服務執行個體可能再也無法取得傳送埠的相關資訊，例如傳送埠的名稱。 雖然這項資訊是由快取得來，但若是服務執行個體必須重新傳送訊息，則此執行個體將無法完成，而訊息也會被擱置。 刪除傳送埠之前, 您應該確認沒有執行中所述，服務執行個體，[如何檢視傳送埠的執行個體資訊](../core/how-to-view-instance-information-for-a-send-port.md)。  
  
 您只有在符合下列條件時，才可以刪除傳送埠：  
  
-   沒有協調流程繫結至此傳送埠。 如果這種情況，您可以依照下列中的指示移除繫結[如何解除繫結協調流程](../core/how-to-unbind-an-orchestration.md)。  
  
-   已停止並取消登錄此傳送埠。 如需停止及取消登錄傳送埠的指示，請參閱[如何取消登錄傳送埠或傳送埠群組](../core/how-to-unenlist-a-send-port-or-send-port-group.md)和[如何停止傳送埠或傳送埠群組](../core/how-to-stop-a-send-port-or-send-port-group.md)。  
  
-   沒有合作對象參考此傳送埠。 如需有關移除從合作對象傳送埠參考的指示，請參閱[如何檢視或編輯合作對象](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca)。  
  
-   此傳送埠沒有包含在傳送埠群組中。 如需從傳送埠群組移除傳送埠的指示，請參閱[如何從傳送埠群組移除傳送埠](../core/how-to-remove-a-send-port-from-a-send-port-group.md)。  
  
> [!NOTE]
>  應用程式開發人員可以在開發過程中刪除傳送埠使用本主題中的程序。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須為 BizTalk Server 系統管理員群組的成員登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-delete-a-send-port"></a>刪除傳送埠  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 BizTalk Server 管理、 BizTalk 群組、 展開 應用程式，然後展開包含您想要刪除的傳送埠的應用程式  
  
3.  按一下**傳送埠**，傳送埠，以滑鼠右鍵按一下，然後按一下**刪除**。  
  
## <a name="see-also"></a>請參閱  
 [建立和設定傳送埠](../core/creating-and-configuring-send-ports.md)