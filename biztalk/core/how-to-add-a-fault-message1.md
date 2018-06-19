---
title: 如何新增錯誤 Message1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exceptions, adding messages
- fault messages, adding
- adding, fault messages
- faults, adding messages
ms.assetid: 9d21de6b-c1a5-46e9-a9dc-d6aa7b5fe34b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87ef85460f6ca6aea046ef9efff60fd198664cd1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246646"
---
# <a name="how-to-add-a-fault-message"></a><span data-ttu-id="d5dba-102">如何新增錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="d5dba-102">How to Add a Fault Message</span></span>
<span data-ttu-id="d5dba-103">您一開始建立連接後端系統的連接埠時，會包含要求和回應。</span><span class="sxs-lookup"><span data-stu-id="d5dba-103">When you first created the port to the back-end system, it contained a request and a response.</span></span> <span data-ttu-id="d5dba-104">您必須新增錯誤以擷取例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d5dba-104">You must add a fault to capture the exception.</span></span>  
  
### <a name="to-add-a-fault-message"></a><span data-ttu-id="d5dba-105">若要新增錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="d5dba-105">To add a fault message</span></span>  
  
1.  <span data-ttu-id="d5dba-106">以滑鼠右鍵按一下**連接埠作業**，然後選取**新錯誤訊息**。</span><span class="sxs-lookup"><span data-stu-id="d5dba-106">Right-click **Port Operation**, and then select a **New Fault Message**.</span></span>  
  
     <span data-ttu-id="d5dba-107">A**錯誤**之下**要求和回應**在連接埠。</span><span class="sxs-lookup"><span data-stu-id="d5dba-107">A **Fault** appears under the **Request and Response** in the port.</span></span>  
  
2.  <span data-ttu-id="d5dba-108">在**協調流程檢視**畫面上，以滑鼠右鍵按一下**訊息**，然後選取**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="d5dba-108">On the **Orchestration View** screen, right-click **Messages**, and then select **New Message**.</span></span>  
  
     <span data-ttu-id="d5dba-109">Message_3 隨即建立，您可將它專門指派給該錯誤。</span><span class="sxs-lookup"><span data-stu-id="d5dba-109">This creates Message_3, which you can assign specifically to the fault.</span></span>  
  
3.  <span data-ttu-id="d5dba-110">以滑鼠右鍵按一下**Message_3**存取**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="d5dba-110">Right-click **Message_3** to access the **Properties** window.</span></span>  
  
    1.  <span data-ttu-id="d5dba-111">設定**訊息類型**。</span><span class="sxs-lookup"><span data-stu-id="d5dba-111">Set the **Message Type**.</span></span>  
  
    2.  <span data-ttu-id="d5dba-112">選取**結構描述**，然後選取從**參考組件**。</span><span class="sxs-lookup"><span data-stu-id="d5dba-112">Select **Schema**, and then select from **ref assembly**.</span></span>  
  
         <span data-ttu-id="d5dba-113">這會開啟**選取成品類型**視窗。</span><span class="sxs-lookup"><span data-stu-id="d5dba-113">This opens a **Select Artifact Type** window.</span></span>  
  
    3.  <span data-ttu-id="d5dba-114">向下捲動並選取完整格式的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d5dba-114">Scroll down and select the fully qualified fault.</span></span>  
  
         <span data-ttu-id="d5dba-115">名稱是**BTS。SOAP_Envelope_1__1.fault**。</span><span class="sxs-lookup"><span data-stu-id="d5dba-115">The name is **BTS.SOAP_Envelope_1__1.fault**.</span></span> <span data-ttu-id="d5dba-116">按一下**確定**接受選擇並關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="d5dba-116">Click **OK** to accept the selection and close the window.</span></span>  
  
4.  <span data-ttu-id="d5dba-117">以滑鼠右鍵按一下**錯誤**存取**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="d5dba-117">Right-click the **Fault** to access the **Properties** window.</span></span>  
  
    1.  <span data-ttu-id="d5dba-118">設定**訊息類型**。</span><span class="sxs-lookup"><span data-stu-id="d5dba-118">Set the **Message Type**.</span></span>  
  
    2.  <span data-ttu-id="d5dba-119">選取**結構描述**，然後選取從**ref**組件。</span><span class="sxs-lookup"><span data-stu-id="d5dba-119">Select **Schema** and then select from **ref** assembly.</span></span>  
  
         <span data-ttu-id="d5dba-120">這會開啟**選取成品類型**視窗。</span><span class="sxs-lookup"><span data-stu-id="d5dba-120">This opens a **Select Artifact Type** window.</span></span>  
  
    3.  <span data-ttu-id="d5dba-121">向下捲動並選取完整格式的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d5dba-121">Scroll down and select the fully qualified fault.</span></span>  
  
         <span data-ttu-id="d5dba-122">名稱是**BTS。SOAP_Envelope_1__1.fault**。</span><span class="sxs-lookup"><span data-stu-id="d5dba-122">The name is **BTS.SOAP_Envelope_1__1.fault**.</span></span>  
  
    4.  <span data-ttu-id="d5dba-123">按一下**確定**接受選擇並關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="d5dba-123">Click **OK** to accept the selection and close the window.</span></span>  
  
         ![](../core/media/siebeladapter-17-exceptionhandling-addscope.gif "SiebelAdapter_17_ExceptionHandling_AddScope")  
  
5.  <span data-ttu-id="d5dba-124">為錯誤命名後，您會將此名稱設定為 CatchException 的例外狀況物件型別。</span><span class="sxs-lookup"><span data-stu-id="d5dba-124">After the fault is named, you will set this name to the CatchException's exception object type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5dba-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5dba-125">See Also</span></span>  
 [<span data-ttu-id="d5dba-126">使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="d5dba-126">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling2.md)