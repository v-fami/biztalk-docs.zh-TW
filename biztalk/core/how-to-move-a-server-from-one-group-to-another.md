---
title: 如何將伺服器從一個群組移至另一個 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- groups, servers
- groups, moving
- managing [groups], moving servers
- servers, moving
- managing [servers], moving
- servers, groups
ms.assetid: 3f789a62-f597-426b-9cea-74c1fe22b694
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c9e5dfdf266d2205283afa7cd9804c31fc93ff3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254566"
---
# <a name="how-to-move-a-server-from-one-group-to-another"></a>如何將伺服器從一個群組移至另一個群組
一部伺服器僅能與一個 BizTalk Server 群組關聯。 若要將伺服器從一個群組移至另一個群組，必須先取消設定此伺服器，從原始群組移除它，然後將它加入新群組中。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序，您必須以「SSO 系統管理員」群組及「Windows 系統管理員」群組的成員身分登入。  
  
### <a name="to-move-a-server-from-one-biztalk-group-to-another"></a>將伺服器從一個 BizTalk 群組移至另一個群組  
  
1.  按一下您想要從 BizTalk 群組移至另一部電腦上**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 組態**.  
  
2.  在功能表列上，按一下 **取消設定功能**。  
  
3.  在**取消設定功能**對話方塊中，選取**企業單一登入**，選取**群組**，然後按一下 **確定**。  
  
    > [!CAUTION]
    >  取消設定群組也會將該電腦上設定的所有相關功能取消設定。  
  
4.  按一下 **[是]**。  
  
5.  在**Microsoft BizTalk Server 組態**視窗中，按一下 **下一步**。  
  
     會取消設定企業 SSO、群組以及它們相依的功能。  
  
6.  按一下 **[完成]**。  
  
7.  在**Microsoft BizTalk Server 組態**視窗中，選取**自訂組態**。  
  
8.  在**資料庫伺服器名稱**，輸入您要移動伺服器之 BizTalk 群組的 SQL server 名稱。  
  
9. 在**服務認證**，輸入適當的使用者名稱和密碼，服務會使用，然後按一下**設定**。  
  
10. 在畫面左側的導覽樹狀目錄中，按一下 **企業單一登入**。  
  
11. 在**企業單一登入**頁面上，按一下**加入現有的 SSO 系統**。  
  
     請確認伺服器名稱和資料庫名稱是指向您要移動伺服器之 BizTalk Server 群組的主要 SSO 資料庫伺服器。  
  
12. 在畫面左側的導覽樹狀目錄中，按一下 **群組**。  
  
13. 在**群組**頁面上，按一下**加入現有的 BizTalk 群組**。  
  
     請確認伺服器名稱和資料庫名稱是指向您要移動伺服器之 BizTalk Server 群組的資料庫。  
  
14. 在功能表列上，按一下 **套用組態**設定這部電腦上的企業單一登入和群組。  
  
## <a name="see-also"></a>另請參閱  
 [管理群組](../core/managing-groups.md)   
 [BizTalk 群組](../core/biztalk-groups.md)   
 [如何將伺服器新增至群組](../core/how-to-add-a-server-to-a-group.md)   
 [如何從群組移除伺服器](../core/how-to-remove-a-server-from-a-group.md)   
 [如何修改群組屬性](../core/how-to-modify-group-properties.md)   
 [處理組態架構](../install-and-config-guides/working-with-the-configuration-framework.md)   
 [如何新增主控件執行個體](../core/how-to-add-a-host-instance.md)   
 [管理伺服器](../core/managing-servers.md)