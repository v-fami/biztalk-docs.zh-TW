---
title: 如何設定追蹤結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- schemas, configuring
- managing [schemas], configuring
- configuring [HAT tracking], schemas
- configuring, schemas
- configuring, tracking
- HAT, schemas
- managing [schemas], tracking
- schemas, tracking
- tracking, configuring
- tracking, schemas
ms.assetid: b5f69c98-8824-43b1-8f21-d84b60ac5431
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: daef2bb1b118388897f98b6c2fa885b7fed4bbc0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000327"
---
# <a name="how-to-configure-tracking-for-a-schema"></a>如何為結構描述設定追蹤
本主題描述如何使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定追蹤結構描述。 若要設定追蹤，您可以指定您想要檢視的查詢檢視中的訊息屬性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台 群組中樞頁面。  
  
 如需有關建立和使用查詢的詳細資訊，請參閱 <<c0> [ 使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md)。 如需有關追蹤功能的訊息事件和服務執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 若您只想檢視追蹤選項，可以用 BizTalk Server 操作員群組的成員身分登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-configure-tracking-for-a-schema"></a>為結構描述設定追蹤  
  
1. 按一下 **開始**，按一下**程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開包含您要設定追蹤的結構描述的 BizTalk 群組，然後再展開包含結構描述的應用程式。  
  
3. 按一下 **結構描述**，以滑鼠右鍵按一下結構描述，然後按一下**屬性**。  
  
4. 在左窗格中，按一下**追蹤**。  
  
5. 執行下列動作，以指定要用於追蹤訊息，哪些屬性其中一個項目，然後按一下**確定**:  
  
   -   選取 **選取所有訊息屬性**核取方塊，以使用所有列出的屬性。  
  
       > [!NOTE]
       >  只包含升級的屬性的結構描述才能使用此核取方塊。  
  
   -   選取每個想要使用屬性的核取方塊。  
  
       > [!NOTE]
       >  這是僅適用於包含升級的屬性的結構描述。  
  
> [!NOTE]
>  您應該只選取需要的選項，因為追蹤訊息會為系統產生效能與存放區的額外負擔。  
  
## <a name="see-also"></a>另請參閱  
 [管理結構描述](../core/managing-schemas.md)