---
title: 如何登錄或取消登錄角色的合作對象 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [role links], enlisting
- enlisting, role links
- role links, unenlisting
- role links, enlisting
- managing [role links], unenlisting
ms.assetid: 06fc2a64-3add-400c-9f9d-fab22fdf5366
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 046e51424427973534d9e4defdbf6e8d58eb8b2f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966247"
---
# <a name="how-to-enlist-or-unenlist-a-party-for-a-role"></a>如何登錄或取消登錄角色的合作對象
本主題描述如何使用 BizTalk Server 管理主控台來登錄或取消登錄角色的合作對象。 登錄角色的合作對象會將合作對象指派給角色，而取消登錄合作對象則會將合作對象從角色中移除。  
  
 當登錄或取消登錄角色的合作對象時，請記住下列重點：  
  
-   您必須先建立合作對象，才可以將它登錄。 如需相關指示，請參閱 <<c0> [ 如何建立合作對象](http://msdn.microsoft.com/library/f6feca1d-bc83-4fb6-981d-26c9e0d53044)。  
  
-   您可以登錄或取消登錄角色的合作對象，而不需重新啟動應用程式。  
  
> [!NOTE]
>  應用程式開發人員可以使用此主題中的程序，在開發程序中登錄或取消登錄合作對象。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-enlist-or-unenlist-a-party-for-a-role"></a>登錄或取消登錄角色的合作對象  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，展開**應用程式**，然後展開包含您要登錄的角色連結的應用程式或取消登錄合作對象。  
  
3. 按一下 **角色連結**，以滑鼠右鍵按一下您要登錄或取消登錄合作對象，並按一下 角色連結**屬性**。  
  
4. 若要登錄合作對象，請執行下列步驟：  
  
   -   按一下 **登錄**按一下要登錄的合作對象。  
  
   -   按一下 **繫結**，請在**傳送連接埠**下拉式清單中，按一下傳送連接埠連接到用於此合作對象，然後按一下 **確定**兩次。  
  
5. 要取消登錄合作對象，按一下 合作對象、 按一下**取消登錄**，然後按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [管理角色連結](../core/managing-role-links.md)