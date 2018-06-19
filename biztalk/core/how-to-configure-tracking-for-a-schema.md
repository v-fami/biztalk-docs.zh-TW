---
title: 如何設定追蹤之結構描述 |Microsoft 文件
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
ms.openlocfilehash: e15cb2210062901786b179ec75fe3880dea660b4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248046"
---
# <a name="how-to-configure-tracking-for-a-schema"></a><span data-ttu-id="26fbd-102">如何為結構描述設定追蹤</span><span class="sxs-lookup"><span data-stu-id="26fbd-102">How to Configure Tracking for a Schema</span></span>
<span data-ttu-id="26fbd-103">本主題描述如何使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定追蹤之結構描述。</span><span class="sxs-lookup"><span data-stu-id="26fbd-103">This topic describes how to use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to configure tracking for a schema.</span></span> <span data-ttu-id="26fbd-104">若要設定追蹤，您可以指定您想要檢視的查詢檢視中的訊息屬性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台 群組中樞頁面。</span><span class="sxs-lookup"><span data-stu-id="26fbd-104">To configure tracking, you specify the properties of the messages that you want to view in the query views of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console Group Hub page.</span></span>  
  
 <span data-ttu-id="26fbd-105">如需有關建立和使用查詢的詳細資訊，請參閱[使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="26fbd-105">For more information about creating and using queries, see [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md).</span></span> <span data-ttu-id="26fbd-106">如需有關追蹤功能的訊息事件和服務執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)。</span><span class="sxs-lookup"><span data-stu-id="26fbd-106">For more information about the message event and service instance tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="26fbd-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="26fbd-107">Prerequisites</span></span>  
 <span data-ttu-id="26fbd-108">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="26fbd-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="26fbd-109">若您只想檢視追蹤選項，可以用 BizTalk Server 操作員群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="26fbd-109">To you want to view tracking options only, you can be logged on as a member of the BizTalk Server Operators group.</span></span> <span data-ttu-id="26fbd-110">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="26fbd-110">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-tracking-for-a-schema"></a><span data-ttu-id="26fbd-111">為結構描述設定追蹤</span><span class="sxs-lookup"><span data-stu-id="26fbd-111">To configure tracking for a schema</span></span>  
  
1.  <span data-ttu-id="26fbd-112">按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="26fbd-112">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="26fbd-113">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開包含您要設定追蹤，結構的描述的 BizTalk 群組，然後再展開包含結構描述的應用程式。</span><span class="sxs-lookup"><span data-stu-id="26fbd-113">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the schema for which you want to configure tracking, and then expand the application containing the schema.</span></span>  
  
3.  <span data-ttu-id="26fbd-114">按一下**結構描述**，結構描述中，以滑鼠右鍵按一下，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="26fbd-114">Click **Schemas**, right-click the schema, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="26fbd-115">在左窗格中，按一下 **追蹤**。</span><span class="sxs-lookup"><span data-stu-id="26fbd-115">In the left pane, click **Tracking**.</span></span>  
  
5.  <span data-ttu-id="26fbd-116">執行下列動作，以指定的屬性，用於追蹤訊息，其中一項，然後按一下**確定**:</span><span class="sxs-lookup"><span data-stu-id="26fbd-116">Do one of the following to specify which properties to use for tracking messages, and then click **OK**:</span></span>  
  
    -   <span data-ttu-id="26fbd-117">選取**選取所有訊息屬性**核取方塊，以使用所有列出的屬性。</span><span class="sxs-lookup"><span data-stu-id="26fbd-117">Select the **Select all message properties** check box to use all the listed properties.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="26fbd-118">此核取方塊是僅適用於包含升級的屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="26fbd-118">This check box is available only for schemas that contain promoted properties.</span></span>  
  
    -   <span data-ttu-id="26fbd-119">選取每個想要使用屬性的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="26fbd-119">Select the check box of each property that you want to use.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="26fbd-120">這是僅適用於包含升級的屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="26fbd-120">This is available only for schemas that contain promoted properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26fbd-121">您應該只選取需要的選項，因為追蹤訊息會為系統產生效能與存放區的額外負擔。</span><span class="sxs-lookup"><span data-stu-id="26fbd-121">You should select only the options you need, as tracking messages creates performance and storage overhead for your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26fbd-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26fbd-122">See Also</span></span>  
 [<span data-ttu-id="26fbd-123">管理結構描述</span><span class="sxs-lookup"><span data-stu-id="26fbd-123">Managing Schemas</span></span>](../core/managing-schemas.md)