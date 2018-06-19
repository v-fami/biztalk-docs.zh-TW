---
title: InfoPath 訊息範本 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4bb055b1-8480-44dd-8739-f2981bca63c3
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b8ec04d16da25f39060540aa8a8205421397d18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295142"
---
# <a name="the-infopath-message-template"></a><span data-ttu-id="f20cb-102">InfoPath 訊息範本</span><span class="sxs-lookup"><span data-stu-id="f20cb-102">The InfoPath Message Template</span></span>
<span data-ttu-id="f20cb-103">ESB 管理入口網站中檢視 ESB 錯誤訊息或者，使用者可以利用名為 ESB 例外狀況訊息檢視器，所提供的 Microsoft InfoPath 訊息範本[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f20cb-103">As an alternative to viewing ESB fault messages in the ESB Management Portal, users can take advantage of a Microsoft InfoPath message template named the ESB Exception Message Viewer, provided with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span>  
  
 <span data-ttu-id="f20cb-104">在 ESB 例外狀況管理架構可以保存訊息的序列化格式，以及 [ESB 例外狀況訊息檢視器] 範本中，將會顯示錯誤訊息和所包含的原始訊息的數個檢視。</span><span class="sxs-lookup"><span data-stu-id="f20cb-104">The ESB Exception Management Framework can persist messages in a serialized format that, together with the ESB Exception Message Viewer template, will display several views of the fault message and the original messages it contains.</span></span> <span data-ttu-id="f20cb-105">ESB 例外狀況訊息檢視器會提供下列檢視：</span><span class="sxs-lookup"><span data-stu-id="f20cb-105">The ESB Exception Message Viewer provides the following views:</span></span>  
  
-   <span data-ttu-id="f20cb-106">一般檢視</span><span class="sxs-lookup"><span data-stu-id="f20cb-106">General view</span></span>  
  
-   <span data-ttu-id="f20cb-107">例外狀況物件的檢視</span><span class="sxs-lookup"><span data-stu-id="f20cb-107">Exception Object view</span></span>  
  
-   <span data-ttu-id="f20cb-108">Messages view (訊息檢視)</span><span class="sxs-lookup"><span data-stu-id="f20cb-108">Messages view</span></span>  
  
 <span data-ttu-id="f20cb-109">圖 1 顯示 ESB 例外狀況訊息檢視器中，這會顯示最環境屬性例外狀況的一般檢視。</span><span class="sxs-lookup"><span data-stu-id="f20cb-109">Figure 1 shows the General view of the ESB Exception Message Viewer, which displays most ambient properties of the exception.</span></span>  
  
 <span data-ttu-id="f20cb-110">![例外狀況訊息的一般檢視](../esb-toolkit/media/ch4-exceptionmessagegeneralview.gif "第 4 章第 ExceptionMessageGeneralView")</span><span class="sxs-lookup"><span data-stu-id="f20cb-110">![Exception Message General View](../esb-toolkit/media/ch4-exceptionmessagegeneralview.gif "Ch4-ExceptionMessageGeneralView")</span></span>  
  
 <span data-ttu-id="f20cb-111">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="f20cb-111">**Figure 1**</span></span>  
  
 <span data-ttu-id="f20cb-112">**ESB 例外狀況訊息檢視器顯示一般檢視**</span><span class="sxs-lookup"><span data-stu-id="f20cb-112">**The ESB Exception Message Viewer showing the General view**</span></span>  
  
 <span data-ttu-id="f20cb-113">圖 2 顯示例外狀況物件檢視中，顯示的內容以及從堆疊追蹤**System.Exception**物件。</span><span class="sxs-lookup"><span data-stu-id="f20cb-113">Figure 2 shows the Exception Object view, which displays the properties and the stack trace from the **System.Exception** object.</span></span>  
  
 <span data-ttu-id="f20cb-114">![例外狀況訊息的例外狀況物件](../esb-toolkit/media/ch4-exceptionmessageexceptionobject.gif "第 4 章第 ExceptionMessageExceptionObject")</span><span class="sxs-lookup"><span data-stu-id="f20cb-114">![Exception Message Exception Object](../esb-toolkit/media/ch4-exceptionmessageexceptionobject.gif "Ch4-ExceptionMessageExceptionObject")</span></span>  
  
 <span data-ttu-id="f20cb-115">**圖 2**</span><span class="sxs-lookup"><span data-stu-id="f20cb-115">**Figure 2**</span></span>  
  
 <span data-ttu-id="f20cb-116">**顯示例外狀況物件檢視 ESB 例外狀況訊息檢視器**</span><span class="sxs-lookup"><span data-stu-id="f20cb-116">**The ESB Exception Message Viewer showing the Exception Object view**</span></span>  
  
 <span data-ttu-id="f20cb-117">圖 3 顯示的訊息檢視中，提供下拉式清單，使用者可以從中選取從可用的持續性訊息。</span><span class="sxs-lookup"><span data-stu-id="f20cb-117">Figure 3 shows the Messages view, which provides a drop-down list from which the user can select from available persisted messages.</span></span> <span data-ttu-id="f20cb-118">檢視會顯示保存的訊息和 XML 訊息內容的內容屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f20cb-118">The view displays the values of the context properties of the persisted message and the XML message content.</span></span>  
  
 <span data-ttu-id="f20cb-119">![例外狀況訊息的訊息檢視](../esb-toolkit/media/ch4-exceptionmessagemessagesview.gif "第 4 章第 ExceptionMessageMessagesView")</span><span class="sxs-lookup"><span data-stu-id="f20cb-119">![Exception Message Messages View](../esb-toolkit/media/ch4-exceptionmessagemessagesview.gif "Ch4-ExceptionMessageMessagesView")</span></span>  
  
 <span data-ttu-id="f20cb-120">**圖 3**</span><span class="sxs-lookup"><span data-stu-id="f20cb-120">**Figure 3**</span></span>  
  
 <span data-ttu-id="f20cb-121">**ESB 例外狀況訊息檢視器顯示的訊息檢視**</span><span class="sxs-lookup"><span data-stu-id="f20cb-121">**The ESB Exception Message Viewer showing the Messages view**</span></span>