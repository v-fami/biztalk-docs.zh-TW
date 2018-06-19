---
title: 如何檢視結構描述的結構描述定義 (XSD) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- schemas, viewing
- managing [schemas], viewing
- viewing, schema definitions
- schemas, schema definition (XSD)
- managing [schemas], schema definition (XSD)
ms.assetid: 21b6d9e6-5737-4334-9fe6-15ae01f90c0d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 941951398ec966dea0045283e13c4581f60016aa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256438"
---
# <a name="how-to-view-the-schema-definition-xsd-of-a-schema"></a><span data-ttu-id="82e7e-102">如何檢視結構描述的結構描述定義 (XSD)</span><span class="sxs-lookup"><span data-stu-id="82e7e-102">How to View the Schema Definition (XSD) of a Schema</span></span>
<span data-ttu-id="82e7e-103">本主題描述如何使用 BizTalk Server 管理主控台，檢視結構描述的結構描述定義 (XSD)。</span><span class="sxs-lookup"><span data-stu-id="82e7e-103">This topic describes how to use the BizTalk Server Administration console to view the schema definition (XSD) of a schema.</span></span> <span data-ttu-id="82e7e-104">為了疑難排解結構描述的驗證錯誤，或驗證是否已部署正確的結構描述，您可能會想要這樣做。</span><span class="sxs-lookup"><span data-stu-id="82e7e-104">You might want to do this to troubleshoot schema validation errors or validate that the correct schema is deployed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="82e7e-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="82e7e-105">Prerequisites</span></span>  
 <span data-ttu-id="82e7e-106">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組或「BizTalk Server 操作員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="82e7e-106">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group or BizTalk Server Operators group.</span></span> <span data-ttu-id="82e7e-107">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="82e7e-107">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-view-the-xsd-of-a-schema"></a><span data-ttu-id="82e7e-108">若要檢視結構描述的 XSD</span><span class="sxs-lookup"><span data-stu-id="82e7e-108">To view the XSD of a schema</span></span>  
  
1.  <span data-ttu-id="82e7e-109">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="82e7e-109">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="82e7e-110">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開包含您想要檢視 XSD 之結構的描述的 BizTalk 群組，然後再展開包含結構描述的應用程式。</span><span class="sxs-lookup"><span data-stu-id="82e7e-110">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the schema for which you want to view the XSD, and then expand the application containing the schema.</span></span>  
  
3.  <span data-ttu-id="82e7e-111">按一下**結構描述**，結構描述中，以滑鼠右鍵按一下，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="82e7e-111">Click **Schemas**, right-click the schema, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="82e7e-112">在左窗格中，按一下 **結構描述檢視**。</span><span class="sxs-lookup"><span data-stu-id="82e7e-112">In the left pane, click **Schema View**.</span></span>  
  
     <span data-ttu-id="82e7e-113">XSD 隨即顯示在右窗格中。</span><span class="sxs-lookup"><span data-stu-id="82e7e-113">The XSD displays in the right pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e7e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82e7e-114">See Also</span></span>  
 [<span data-ttu-id="82e7e-115">管理結構描述</span><span class="sxs-lookup"><span data-stu-id="82e7e-115">Managing Schemas</span></span>](../core/managing-schemas.md)