---
title: 如何變更預設的應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications, default
- applications, modifying
- modifying, applications
ms.assetid: cfa5e88f-0bbb-4edd-a840-722dcdcce266
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b4122b7ab0581be974ee1fdd38ba2cc3ddbc41e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986551"
---
# <a name="how-to-change-the-default-application"></a>如何變更預設應用程式
本主題說明如何透過在 BizTalk Server 管理主控台中編輯應用程式的屬性，變更預設的應用程式。 您也可以變更預設的應用程式建立新的應用程式並將它指定為預設應用程式中所述[如何建立應用程式](../core/how-to-create-an-application.md)。  
  
 安裝 BizTalk Sever 時，系統會在 BizTalk 管理資料庫中建立一個名為 BizTalk Application 1 的預設應用程式，並將它顯示在 BizTalk Server 管理主控台中。 當您從舊版的 BizTalk Server 進行升級時，您的成品會自動放入此應用程式中。 此外，如果您使用 BTSTask 匯入 Windows Installer (.msi) 檔案，但未指定應用程式，.msi 檔案中的成品也會匯入此預設應用程式中。  
  
 您不能刪除預設應用程式，但是可以變更預設的應用程式。 變更預設應用程式後，您就可以視需要刪除先前的預設應用程式。 如需相關指示，請參閱 <<c0> [ 如何從 BizTalk 群組刪除 BizTalk 應用程式](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md)。  
  
 變更預設應用程式時，所有的成品都會保留在原始的預設應用程式中。 如果需要，您也可以從應用程式中明確移出這些成品。 如需相關指示，請參閱 <<c0> [ 如何將成品移至不同的應用程式](../core/how-to-move-an-artifact-to-a-different-application.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-change-the-default-application"></a>若要變更預設應用程式  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 BizTalk 群組、 以滑鼠右鍵按一下您想要設成預設值，然後按一下 應用程式**屬性**。  
  
3. 選取 **將此設為預設應用程式**核取方塊，然後按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)