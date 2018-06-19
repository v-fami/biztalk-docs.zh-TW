---
title: MQSeries 配接器的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c36bcabb-e1eb-455c-8384-00d4682464d3
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe3093416a10b6b66867dcb2e3629de8f25e5aca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262198"
---
# <a name="known-issues-with-the-mqseries-adapter"></a><span data-ttu-id="b188a-102">MQSeries 配接器的已知問題</span><span class="sxs-lookup"><span data-stu-id="b188a-102">Known Issues with the MQSeries Adapter</span></span>
<span data-ttu-id="b188a-103">本節包含可幫助您避免錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="b188a-103">This section contains information that may help you avoid errors.</span></span>  
  
## <a name="know-issues"></a><span data-ttu-id="b188a-104">已知問題</span><span class="sxs-lookup"><span data-stu-id="b188a-104">Know Issues</span></span>  
  
#### <a name="access-denied-errors-occur-when-attempting-to-send-or-receive-messages"></a><span data-ttu-id="b188a-105">試圖傳送或接收訊息時，發生拒絕存取的錯誤</span><span class="sxs-lookup"><span data-stu-id="b188a-105">Access Denied errors occur when attempting to send or receive messages</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="b188a-106">問題</span><span class="sxs-lookup"><span data-stu-id="b188a-106">Problem</span></span>  
 <span data-ttu-id="b188a-107">當您使用 MQSeries 配接器傳送訊息到 MQSeries 伺服器或接收來自 MQSeries 伺服器的訊息時，事件檢視器中的應用程式記錄檔會記錄類似下列的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="b188a-107">When you use the MQSeries adapter to send messages to or receive messages from an MQSeries server, error messages that are similar to the following are logged in the Application log in Event Viewer:</span></span>  
  
```  
The adapter "MQSeries" raised an error message. Details "The adapter has encountered an 'Access Denied' error while attempting to contact the COM+ object on the MQSeries server. Ensure the BizTalk account is added to the Role on the MQSAgent COM+ application."  
```  
  
```  
The adapter failed to transmit message going to send port "MQS://servername/queuename". It will be retransmitted after the retry interval specified for this Send Port. Details: "The adapter has encountered an 'Access Denied' error while attempting to contact the COM+ object on the MQSeries server. Ensure the BizTalk account is added to the Role on the MQSAgent COM+ application."  
```  
  
> [!NOTE]
>  <span data-ttu-id="b188a-108">此錯誤訊息中*servername*是伺服器的名稱和*queuename*是佇列的名稱。</span><span class="sxs-lookup"><span data-stu-id="b188a-108">In this error message, *servername* is the name of the server and *queuename* is the name of the queue.</span></span>  
  
 <span data-ttu-id="b188a-109">此外，當您嘗試建立設定為使用 BizTalk Adapter for MQSeries 的接收位置或傳送埠時，可能會在事件檢視器中收到下列警告訊息：</span><span class="sxs-lookup"><span data-stu-id="b188a-109">Additionally, when you try to create the receive location or the send port that is configured to use the BizTalk Adapter for MQSeries, you may receive the following warning message in Event Viewer:</span></span>  
  
```  
The adapter "MQSeries" raised an error message. Details "The adapter has encountered an 'Access Denied' error while attempting to contact the COM+ object on the MQSeries server. Ensure the BizTalk account is added to the Role on the MQSAgent COM+ application."  
```  
  
##### <a name="cause"></a><span data-ttu-id="b188a-110">原因</span><span class="sxs-lookup"><span data-stu-id="b188a-110">Cause</span></span>  
 <span data-ttu-id="b188a-111">如果下列一或多個狀況成立，可能就會發生這個問題：</span><span class="sxs-lookup"><span data-stu-id="b188a-111">This issue may occur if one or more of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="b188a-112">MQSeries 配接器的主控件帳戶沒有 MQSeries 伺服器上 MQSAgent COM+ 應用程式的必要權限。</span><span class="sxs-lookup"><span data-stu-id="b188a-112">The host account for the MQSeries adapter does not have the required permissions for the MQSAgent COM+ application on the MQSeries server.</span></span>  
  
-   <span data-ttu-id="b188a-113">在 [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 伺服器上，MQSeries 配接器的主控件帳戶不是 MQSeries 伺服器上分散式 COM 使用者群組的成員。</span><span class="sxs-lookup"><span data-stu-id="b188a-113">On a [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]-based server, the host account for the MQSeries adapter is not a member of the Distributed COM Users group on the MQSeries server.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="b188a-114">解決方案</span><span class="sxs-lookup"><span data-stu-id="b188a-114">Resolution</span></span>  
 <span data-ttu-id="b188a-115">若要解決此問題，請使用下列方法。</span><span class="sxs-lookup"><span data-stu-id="b188a-115">To resolve this issue, use the following methods.</span></span> <span data-ttu-id="b188a-116">如果其中一個方法無法解決問題，請嘗試使用下一個方法。</span><span class="sxs-lookup"><span data-stu-id="b188a-116">If a method does not resolve the issue, try the next method.</span></span>  
  
 <span data-ttu-id="b188a-117">**方法 1： 啟用網路 COM + 存取 microsoft[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]或[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]為基礎的電腦**</span><span class="sxs-lookup"><span data-stu-id="b188a-117">**Method 1: Enable network COM+ access on the Microsoft [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]-based computer**</span></span>  
  
 <span data-ttu-id="b188a-118">Microsoft 上啟用網路 COM + 存取[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]或[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]-依電腦所述的步驟[如何啟用網路 COM + 存取在 Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=67076)。</span><span class="sxs-lookup"><span data-stu-id="b188a-118">Enable network COM+ access on a Microsoft [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]-based computer by following the steps documented in [How to enable network COM+ access in Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=67076).</span></span>  
  
 <span data-ttu-id="b188a-119">**方法 2： 設定 MSDTC 設定**</span><span class="sxs-lookup"><span data-stu-id="b188a-119">**Method 2: Configure MSDTC settings**</span></span>  
  
 <span data-ttu-id="b188a-120">請依照**上設定適當的 MSDTC 安全性組態選項[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]** 區段[疑難排解 MSDTC 問題的](../core/troubleshooting-problems-with-msdtc.md)設定 MSDTC 設定。</span><span class="sxs-lookup"><span data-stu-id="b188a-120">Follow the steps in the **Set the appropriate MSDTC Security Configuration options on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]** section of [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md) to configure MSDTC settings.</span></span>  
  
 <span data-ttu-id="b188a-121">**方法 3： 確認主控件帳戶已新增至 MQSAgent COM + 應用程式中的角色**</span><span class="sxs-lookup"><span data-stu-id="b188a-121">**Method 3: Verify that the host account is added to the role in the MQSAgent COM+ application**</span></span>  
  
 <span data-ttu-id="b188a-122">確認 MQSeries 配接器的主控件帳戶已新增至 MQSeries 伺服器的 MQSAgent COM+ 應用程式中建立的角色。</span><span class="sxs-lookup"><span data-stu-id="b188a-122">Verify that the host account for the MQSeries adapter is added to the role that was created in the MQSAgent COM+ application on the MQSeries server.</span></span> <span data-ttu-id="b188a-123">您可以在「元件服務」管理主控台介面中進行確認。</span><span class="sxs-lookup"><span data-stu-id="b188a-123">You can verify this in the Component Services management console interface.</span></span>  
  
 <span data-ttu-id="b188a-124">**方法 4： 確認 MQSeries 配接器的主控件帳戶是分散式 COM 使用者群組的成員**</span><span class="sxs-lookup"><span data-stu-id="b188a-124">**Method 4: Verify that the host account for the MQSeries adapter is a member of the Distributed COM Users group**</span></span>  
  
 <span data-ttu-id="b188a-125">在 Windows[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]或[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]-型伺服器，檢查 MQSeries 配接器的主控件帳戶的群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="b188a-125">On a Windows [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]-based server, examine the group memberships of the host account for the MQSeries adapter.</span></span> <span data-ttu-id="b188a-126">請確定帳戶的成員**Distributed COM Users** MQSAgent COM + 應用程式安裝所在的 MQSeries 伺服器上的群組。</span><span class="sxs-lookup"><span data-stu-id="b188a-126">Make sure that the account is a member of the **Distributed COM Users** group on the MQSeries server where the MQSAgent COM+ application is installed.</span></span>  
  
 <span data-ttu-id="b188a-127">如需有關 DCOM 安全性增強功能，在 Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，請參閱[DCOM 安全性增強功能](http://go.microsoft.com/fwlink/?LinkId=67077)。</span><span class="sxs-lookup"><span data-stu-id="b188a-127">For more information about DCOM security enhancements in Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], see [DCOM Security Enhancements](http://go.microsoft.com/fwlink/?LinkId=67077).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b188a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b188a-128">See Also</span></span>  
 [<span data-ttu-id="b188a-129">MQSeries 配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="b188a-129">Troubleshooting the MQSeries Adapter</span></span>](../core/troubleshooting-the-mqseries-adapter.md)