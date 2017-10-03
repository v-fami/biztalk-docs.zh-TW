---
title: "如何從群組移除伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- groups, servers
- managing [groups], deleting servers
- servers, deleting
- deleting, groups
- servers
- managing [servers], deleting from groups
- groups, deleting
- servers, groups
- deleting, servers
ms.assetid: 85596e18-fa17-4f44-bc20-2e4cb578e109
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b69eb694da320e598c7d0cfe5a03d58e0a723a8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-server-from-a-group"></a>如何從群組移除伺服器
一部伺服器僅能與一個 BizTalk 群組關聯。 如果伺服器已經屬於其他群組，您必須先從目前的群組移除該伺服器，才可將其新增至新群組。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序，您必須以「Windows 系統管理員」群組的成員身分登入。  
  
### <a name="to-remove-a-server-from-a-group"></a>從群組移除伺服器  
  
1.  您想要從 BizTalk Server 群組中移除的電腦，按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 組態**.  
  
2.  在功能表列上，按一下 **取消設定功能**。  
  
3.  在**取消設定功能**對話方塊中，選取**群組**，然後按一下 **確定**。  
  
    > [!CAUTION]
    >  取消設定群組也會將該電腦上設定的所有相關功能取消設定。  
  
4.  按一下 **[是]**。  
  
5.  在 Microsoft BizTalk Server 組態精靈中，按一下 **下一步**。  
  
     群組和其相依的功能已取消設定。  
  
6.  按一下 **[完成]**。  
  
## <a name="see-also"></a>另請參閱  
 [管理群組](../core/managing-groups.md)   
 [BizTalk 群組](../core/biztalk-groups.md)   
 [如何將伺服器新增至群組](../core/how-to-add-a-server-to-a-group.md)   
 [如何將伺服器從一個群組移至另一個](../core/how-to-move-a-server-from-one-group-to-another.md)   
 [如何修改群組屬性](../core/how-to-modify-group-properties.md)   
 [管理伺服器](../core/managing-servers.md)