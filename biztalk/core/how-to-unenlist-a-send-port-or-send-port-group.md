---
title: 如何取消登錄傳送埠或傳送埠群組 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unenlisting, send port groups
- send port groups, unenlisting
- managing [send ports], unenlisting
- managing [send port groups], unenlisting
- unenlisting, send ports
- send ports, unenlisting
ms.assetid: 3185adad-2efa-4abd-a532-77ae6c7b4c1d
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac2599ae3d06a75506de244a4f996a9e77cef6ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256670"
---
# <a name="how-to-unenlist-a-send-port-or-send-port-group"></a>如何取消登錄傳送埠或傳送埠群組
本主題描述如何使用 BizTalk Server 管理主控台來取消登錄傳送埠或傳送埠群組。 取消登錄傳送埠或傳送埠群組會刪除與傳送埠或傳送埠群組相關的所有訂閱。 您可以同時取消登錄正在執行和已停止的傳送埠或傳送埠群組。 取消登錄傳送埠或傳送埠群組會自動停止它。  
  
 例如，您可能想要取消登錄傳送埠或傳送埠群組以編輯其繫結，或想要從 BizTalk Server 環境移除傳送埠或傳送埠群組。  
  
 對於已經登錄或正在執行的傳送埠群組，您無法取消登錄其中最近一次登錄的傳送埠。 取消登錄傳送埠群組不會變更其中包含的任何傳送埠的狀態。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-unenlist-a-send-port-or-send-port-group"></a>取消登錄傳送埠或傳送埠群組  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 依序展開 BizTalk 群組、 展開**應用程式**，然後展開包含傳送埠或傳送埠群組，您想要的應用程式取消登錄。  
  
3.  按一下**傳送埠**或**傳送埠群組**，傳送埠或傳送埠群組，以滑鼠右鍵按一下，然後按一下**取消登錄**。  
  
## <a name="see-also"></a>另請參閱  
 [管理傳送埠與傳送埠群組](../core/managing-send-ports-and-send-port-groups.md)