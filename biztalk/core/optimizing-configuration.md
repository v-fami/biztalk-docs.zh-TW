---
redirect_url: /biztalk/core/creating-peoplesoft-send-handlers/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: 2b0a1aa81971e3e086881e23bcfd6d7ba5d5799d
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24012877"
---
# <a name="optimize-configuration"></a><span data-ttu-id="f6fa8-101">最佳化組態</span><span class="sxs-lookup"><span data-stu-id="f6fa8-101">Optimize configuration</span></span>
<span data-ttu-id="f6fa8-102">本節內容包含如何最佳化 BizTalk Adapter for PeopleSoft Enterprise 組態的相關資訊，並且包含設定配接器時所使用參數的說明。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-102">This section contains information about how to optimize your configuration of BizTalk Adapter for PeopleSoft Enterprise and includes parameter descriptions for setting up the adapter.</span></span>  
  
## <a name="message-overload-protection"></a><span data-ttu-id="f6fa8-103">訊息多載保護</span><span class="sxs-lookup"><span data-stu-id="f6fa8-103">Message Overload Protection</span></span>  
 <span data-ttu-id="f6fa8-104">`Max Concurrent Calls` 參數是一項可讓您最佳化組態的功能。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-104">The `Max Concurrent Calls` parameter is a feature that enables you to optimize your configuration.</span></span> <span data-ttu-id="f6fa8-105">您可以在輸送量超過後端處理能力的情況下使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-105">You use this parameter in instances where the throughput exceeds back-end processing capabilities.</span></span> <span data-ttu-id="f6fa8-106">您可以將參數新增到中的配接器**傳送埠傳輸屬性**對話方塊，即可啟動訊息多載保護。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-106">You can add the parameter to the adapters in the **Send Port Transport Properties** dialog box to activate message overload protection.</span></span> <span data-ttu-id="f6fa8-107">預設值為 -1，表示呼叫沒有上限。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-107">The default is -1, meaning the calls are unlimited.</span></span>  
  
 <span data-ttu-id="f6fa8-108">當 BizTalk Server 提交訊息給傳輸配接器時，它會先從配接器接收批次，然後在該批次上叫用 `TransmitMessage()` 來傳輸每個訊息。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-108">When BizTalk Server submits messages to the transmit adapter, it first receives a batch from the adapter and invokes `TransmitMessage()` on the batch to transmit each message.</span></span> <span data-ttu-id="f6fa8-109">完成傳輸時，BizTalk Server 會在批次上叫用 `Done()`，這時配接器就會開始將訊息傳輸至後端。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-109">When done, BizTalk Server invokes `Done()` on the batch, and the adapter starts transmitting the messages to the back-end.</span></span> <span data-ttu-id="f6fa8-110">如果 BizTalk Server 在叫用 `Done` 之前會取得多個批次，`Done` 命令可能就永遠不會發生。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-110">If BizTalk Server obtains multiple batches before `Done` is invoked, the `Done` command might never occur.</span></span> <span data-ttu-id="f6fa8-111">藉由設定批次中的訊息數目上限，您便可以控制送到後端的訊息。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-111">By setting the maximum number of messages in a batch, you can control messages to the back-end.</span></span> <span data-ttu-id="f6fa8-112">此參數的變更會立刻生效。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-112">Changing this parameter takes effect in a minute.</span></span> <span data-ttu-id="f6fa8-113">BizTalk Server 必須擷取 SQL 資料庫中儲存的配接器組態變更。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-113">BizTalk Server must retrieve the changes to the adapter configuration that is saved in the SQL database.</span></span>  
  
## <a name="change-the-max-concurrent-calls-parameter"></a><span data-ttu-id="f6fa8-114">變更同時呼叫數目上限參數</span><span class="sxs-lookup"><span data-stu-id="f6fa8-114">Change the Max Concurrent Calls parameter</span></span>  
  
1.  <span data-ttu-id="f6fa8-115">在**傳送埠傳輸屬性**對話方塊方塊中，輸入**連接**值。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-115">In the **Send Port Transport Properties** dialog box, enter a **Connection** value.</span></span>  
  
     <span data-ttu-id="f6fa8-116">預設值為 40 個工作階段。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-116">The default value is 40 sessions.</span></span> <span data-ttu-id="f6fa8-117">如果您使用較小的值，則可能會遇到執行階段效能降低的情形。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-117">If you use a smaller value, you might experience degradation in run-time performance.</span></span> <span data-ttu-id="f6fa8-118">使用較大的值也是一樣，因為較大的值會超出伺服器的能力，而造成執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-118">The opposite is also true; a bigger value could exceed the ability of the server and result in run-time errors.</span></span>  
  
2.  <span data-ttu-id="f6fa8-119">選取**是**如**重新整理代理程式**強制 runtimeagent.exe 和 browsingagent.exe 程序在必要時自動重新啟動。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-119">Select **Yes** for **Refresh Agent** to force the runtimeagent.exe and the browsingagent.exe processes to restart automatically when required.</span></span>  
  
     <span data-ttu-id="f6fa8-120">例如，您希望處理程序在與伺服器中斷連線時自動重新啟動，或是您在伺服器加上其他項目，但是該項目並未出現在 Microsoft 配接器精靈的選項中。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-120">For example, you want the process to restart automatically if it loses connection with the server, or if you add something to the server and it does not appear in the Microsoft Adapter Wizard for selection.</span></span>  
  
     <span data-ttu-id="f6fa8-121">**重新整理代理程式**參數會重新整理瀏覽與執行階段代理程式。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-121">The **Refresh Agent** parameter refreshes both the browsing and the run-time agents.</span></span> <span data-ttu-id="f6fa8-122">runtimeagent.exe 會在一分鐘之後或是下一次呼叫 Send 時更新。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-122">The runtimeagent.exe updates after a delay of one minute or at the next send call.</span></span>  
  
3.  <span data-ttu-id="f6fa8-123">提供認證以存取 PeopleSoft 系統。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-123">Provide credentials to access the PeopleSoft system.</span></span>  
  
     <span data-ttu-id="f6fa8-124">您可以透過兩種方式來存取系統：</span><span class="sxs-lookup"><span data-stu-id="f6fa8-124">You can use two methods to access the system:</span></span>  
  
    -   <span data-ttu-id="f6fa8-125">登入認證 (傳輸屬性登入參數)</span><span class="sxs-lookup"><span data-stu-id="f6fa8-125">Login Credentials (Transport Properties Login parameters)</span></span>  
  
    -   <span data-ttu-id="f6fa8-126">單一登入 (SSO)</span><span class="sxs-lookup"><span data-stu-id="f6fa8-126">Single Sign-On</span></span>  
  
4.  <span data-ttu-id="f6fa8-127">選取**是**如**使用 SSO**使用單一登入。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-127">Select **Yes** for **Use SSO** to use Single Sign-On.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f6fa8-128">如需詳細資訊，請參閱[安全配接器](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-128">For more information, see [Secure the adapter](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md).</span></span> 
  
5.  <span data-ttu-id="f6fa8-129">在清單中選取分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-129">Select an affiliate application in the list.</span></span>  
  
     <span data-ttu-id="f6fa8-130">由企業單一登入工具所建立的分支機構應用程式，代表像是 PeopleSoft 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-130">An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as PeopleSoft.</span></span> <span data-ttu-id="f6fa8-131">Microsoft BizTalk Adapter for PeopleSoft Enterprise 會使用應用程式使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-131">Microsoft BizTalk Adapter for PeopleSoft Enterprise uses the credentials of an application user.</span></span> <span data-ttu-id="f6fa8-132">這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 資料庫中擷取所得。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-132">These credentials are retrieved from the SSO database for the server system for a specified affiliate application.</span></span> <span data-ttu-id="f6fa8-133">這些認證就是啟動 BizTalk 專案之使用者 (應用程式使用者) 的認證。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-133">The credentials are those of the user (the application user) who launched the BizTalk project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f6fa8-134">如需如何建立分支機構應用程式的詳細資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications2.md)，或 Microsoft BizTalk Server 線上說明。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-134">For more information about how to create affiliate applications, see [Creating Affiliate Applications](../core/creating-affiliate-applications2.md), or the Microsoft BizTalk Server online Help.</span></span>  
  
6.  <span data-ttu-id="f6fa8-135">提供所有必要的資訊，以採用連線資訊之後, 按一下**套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-135">After providing all required information to accept the connection information, click **Apply**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="f6fa8-136">您必須設定連線參數，讓 BizTalk Adapter for PeopleSoft Enterprise 能夠存取 PeopleSoft。</span><span class="sxs-lookup"><span data-stu-id="f6fa8-136">You must set connection parameters for the BizTalk Adapter for PeopleSoft Enterprise to access PeopleSoft.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6fa8-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6fa8-137">See Also</span></span>  
 [<span data-ttu-id="f6fa8-138">建立 PeopleSoft 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="f6fa8-138">Creating PeopleSoft Send Handlers</span></span>](../core/creating-peoplesoft-send-handlers.md)