---
title: 如何將伺服器新增到群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- groups, servers
- adding, servers
- managing [groups], adding servers
- servers, groups
- managing [servers], adding to groups
ms.assetid: 6eca1eeb-1a56-4470-b3bc-c64865cf6270
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8edccbd9bec7c4ef027b1e185e3af6e56a19340
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979367"
---
# <a name="how-to-add-a-server-to-a-group"></a>如何將伺服器新增至群組
您可以使用「BizTalk 伺服器組態」，將伺服器新增至 BizTalk 群組。 將額外的伺服器新增至 BizTalk 群組，可擴充您的 BizTalk Server 環境。  
  
 一部伺服器僅能與一個 BizTalk 群組關聯。 如果伺服器已經屬於其他群組，您必須先從目前的群組移除該伺服器，才可將其新增至新群組。 從 BizTalk 群組移除伺服器的詳細資訊，請參閱[如何從群組移除伺服器](../core/how-to-remove-a-server-from-a-group.md)。  
  
> [!NOTE]
>  與 BizTalk Server 環境中不同伺服器建立關聯的 BizTalk 群組，除了交換訊息之外並不會互動。  
  
> [!IMPORTANT]
>  BizTalk Server 執行階段必須安裝在您想新增至 BizTalk 群組的電腦上。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序，您必須以「SSO 系統管理員」群組及「Windows 系統管理員」群組的成員身分登入。  
  
### <a name="to-add-a-server-to-a-biztalk-group"></a>將伺服器新增至 BizTalk 群組  
  
1. 您想要新增至 BizTalk Server 群組的電腦，按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 組態**.  
  
2. 在  **Microsoft BizTalk Server 組態**，選取**自訂組態**。  
  
3. 在 **資料庫伺服器名稱**，輸入伺服器正要加入 BizTalk 群組的 SQL server 名稱。  
  
4. 在 **服務認證**，輸入適當的使用者名稱和密碼，服務會使用，然後按一下**設定**。  
  
5. 在畫面左側的導覽樹狀目錄中，按一下**企業 SSO**。  
  
6. 在 **企業單一登入**頁面上，按一下**加入現有的 SSO 系統**。  
  
    請確認伺服器名稱和資料庫名稱是指向伺服器正要連結之 BizTalk Server 群組的主要 SSO 資料庫伺服器。  
  
7. 在畫面左側的導覽樹狀目錄中，按一下**群組**。  
  
8. 在 **群組**頁面上，按一下**加入現有的 BizTalk 群組**。  
  
    請確認伺服器名稱和資料庫名稱是指向伺服器正要連結之 BizTalk Server 群組的資料庫。  
  
9. 在功能表列上，按一下**套用組態**來設定 這台電腦上的 企業單一登入和群組。  
  
## <a name="see-also"></a>另請參閱  
 [處理組態架構](../install-and-config-guides/working-with-the-configuration-framework.md)   
 [管理群組](../core/managing-groups.md)   
 [BizTalk 群組](../core/biztalk-groups.md)   
 [如何將伺服器從一個群組移到另一個](../core/how-to-move-a-server-from-one-group-to-another.md)   
 [如何從群組移除伺服器](../core/how-to-remove-a-server-from-a-group.md)   
 [如何修改群組屬性](../core/how-to-modify-group-properties.md)   
 [管理伺服器](../core/managing-servers.md)