---
title: 如何顯示和隱藏屬性結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [schemas], showing
- schemas, properties
- managing [schemas], hiding
- managing [schemas], properties
ms.assetid: e7cc1838-cc3f-4dd3-a7d1-e66e7ee82d0c
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c5cc4708692e659019cf8d95a18868929f75654
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985399"
---
# <a name="how-to-show-and-hide-property-schemas"></a><span data-ttu-id="9c84b-102">如何顯示和隱藏屬性結構描述</span><span class="sxs-lookup"><span data-stu-id="9c84b-102">How to Show and Hide Property Schemas</span></span>
<span data-ttu-id="9c84b-103">本主題描述如何使用 BizTalk Server 管理主控台來顯示及隱藏應用程式結構描述中的屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="9c84b-103">This topic describes how to use the BizTalk Server Administration console to show and hide property schemas in the Schemas folder for an application.</span></span> <span data-ttu-id="9c84b-104">屬性結構描述是 BizTalk 結構描述的簡單版本，在執行個體訊息與訊息內容之間來回複製升級屬性的過程中會使用到。</span><span class="sxs-lookup"><span data-stu-id="9c84b-104">A property schema is a simple version of a BizTalk schema that plays a role in the process of copying promoted properties back and forth between the instance message and the message context.</span></span> <span data-ttu-id="9c84b-105">您可能會想要隱藏屬性結構描述以簡化結構描述檢視，使您只能看到文件結構描述。</span><span class="sxs-lookup"><span data-stu-id="9c84b-105">You might want to hide property schemas to simplify the schema view, so that you only see document schemas.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9c84b-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="9c84b-106">Prerequisites</span></span>  
 <span data-ttu-id="9c84b-107">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組或「BizTalk Server 操作員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="9c84b-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group or BizTalk Server Operators group.</span></span> <span data-ttu-id="9c84b-108">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="9c84b-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-show-or-hide-property-schemas-in-the-schemas-folder"></a><span data-ttu-id="9c84b-109">顯示和隱藏結構描述資料夾中的屬性結構描述</span><span class="sxs-lookup"><span data-stu-id="9c84b-109">To show or hide property schemas in the Schemas folder</span></span>  
  
1. <span data-ttu-id="9c84b-110">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="9c84b-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="9c84b-111">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開包含您要顯示或隱藏屬性結構描述，結構描述資料夾的 BizTalk 群組，然後再展開包含結構描述資料夾的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9c84b-111">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the schemas folder in which you want to show or hide property schemas, and then expand the application containing the schemas folder.</span></span>  
  
3. <span data-ttu-id="9c84b-112">以滑鼠右鍵按一下**結構描述**資料夾中，按一下**隱藏屬性結構描述**或是**顯示屬性結構描述**。</span><span class="sxs-lookup"><span data-stu-id="9c84b-112">Right-click the **Schemas** folder, and click either **Hide Property Schemas** or **Show Property Schemas**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c84b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c84b-113">See Also</span></span>  
 [<span data-ttu-id="9c84b-114">管理結構描述</span><span class="sxs-lookup"><span data-stu-id="9c84b-114">Managing Schemas</span></span>](../core/managing-schemas.md)