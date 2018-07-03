---
title: ApplicationAdapter |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f9b876b-cd37-4e24-a476-186adc155ac0
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b7a754b044fb12bf7cec9fed0e5455e6192c072
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974927"
---
# <a name="applicationadapter"></a><span data-ttu-id="26cf4-102">ApplicationAdapter</span><span class="sxs-lookup"><span data-stu-id="26cf4-102">ApplicationAdapter</span></span>
<span data-ttu-id="26cf4-103">ApplicationAdapter 範例會示範當您收到訊息時，如何從公開程序和私用程序 (回應者或啟動者) 傳送通知。</span><span class="sxs-lookup"><span data-stu-id="26cf4-103">The ApplicationAdapter sample demonstrates how to send notifications from the public and private processes (responder or initiator) when you receive a message.</span></span> <span data-ttu-id="26cf4-104">您可以利用想要的任何其他功能自訂這個範例。</span><span class="sxs-lookup"><span data-stu-id="26cf4-104">You can customize the sample with whatever additional functionality you want.</span></span>  
  
 <span data-ttu-id="26cf4-105">ApplicationAdapter 範例會示範如何實作 `IApplicationAdapter` 類別的 `ApplicationAdapter1` 介面。</span><span class="sxs-lookup"><span data-stu-id="26cf4-105">The ApplicationAdapter sample demonstrates how to implement the `IApplicationAdapter` interface to the `ApplicationAdapter1` class.</span></span> <span data-ttu-id="26cf4-106">這個類別包含 `BeginNotify` 和 `Notify` 這兩個方法。</span><span class="sxs-lookup"><span data-stu-id="26cf4-106">This class includes two methods, `BeginNotify` and `Notify`.</span></span> <span data-ttu-id="26cf4-107">每個類別的參數都是訊息類別、來源合作對象名稱、目的合作對象名稱、夥伴介面程序 (PIP) 代碼、PIP 執行個體識別碼以及 PIP 版本。</span><span class="sxs-lookup"><span data-stu-id="26cf4-107">The parameters for each class are the message category, source party name, destination party name, Partner Interface Process (PIP) code, PIP instance ID, and PIP version.</span></span>  
  
 <span data-ttu-id="26cf4-108">輸入組件名稱和類別名稱設定協議的 ApplicationAdapter**一般**Microsoft® 中的協議索引標籤[!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)]([!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]) 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="26cf4-108">You set the ApplicationAdapter for an agreement by entering the assembly name and class name on the **General** tab of the agreement in the Microsoft® [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] ([!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]) Management Console.</span></span> <span data-ttu-id="26cf4-109">應用程式配接器 .dll 檔會在與 BizTalk 主控件服務相同的認證下執行。</span><span class="sxs-lookup"><span data-stu-id="26cf4-109">The application adapter .dll file runs under the same credentials as the BizTalk host service.</span></span>  
  
 <span data-ttu-id="26cf4-110">如果您變更 ApplicationAdapter 範例或 ApplicationAdapter 範例所依賴的任何外部環境變數，則必須重新啟動裝載 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 公開程序的 BizTalk 主控件服務。</span><span class="sxs-lookup"><span data-stu-id="26cf4-110">If you change the ApplicationAdapter sample or any external environment variable that the ApplicationAdapter sample depends on, restart the BizTalk host service that hosts the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] public process.</span></span>  
  
 <span data-ttu-id="26cf4-111">ApplicationAdapter 範例程式碼位於\<*磁碟機*\>: files\ BizTalk\<版本\>Accelerator for RosettaNet\SDK\ApplicationAdapter\\.</span><span class="sxs-lookup"><span data-stu-id="26cf4-111">The ApplicationAdapter sample code is located at \<*drive*\>:\Program Files\ BizTalk \<version\> Accelerator for RosettaNet\SDK\ApplicationAdapter\\.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="26cf4-112">示範</span><span class="sxs-lookup"><span data-stu-id="26cf4-112">Demonstrates</span></span>  
 <span data-ttu-id="26cf4-113">ApplicationAdapter 範例會示範如何通知回應者私用程序，公開程序已經收到訊息。</span><span class="sxs-lookup"><span data-stu-id="26cf4-113">The ApplicationAdapter sample demonstrates how to notify the responder private process that the public process has received a message.</span></span> <span data-ttu-id="26cf4-114">通知會指示訊息類別、來源合作對象名稱、目的合作對象名稱、PIP 代碼、PIP 版本以及 PIP 執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="26cf4-114">The notification indicates the message category, the source party name, the destination party name, the PIP code, the PIP version, and the PIP instance ID.</span></span> <span data-ttu-id="26cf4-115">您可以對動作或回應訊息傳送這個通知。</span><span class="sxs-lookup"><span data-stu-id="26cf4-115">You can send this notification for either an action or a response message.</span></span>  
  
 <span data-ttu-id="26cf4-116">`BeginNotify` 和 `Notify` 方法的運作方式如下：</span><span class="sxs-lookup"><span data-stu-id="26cf4-116">The `BeginNotify` and `Notify` methods work as follows:</span></span>  
  
1.  <span data-ttu-id="26cf4-117">回應者公開程序會接收訊息。</span><span class="sxs-lookup"><span data-stu-id="26cf4-117">The responder public process receives a message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="26cf4-118">下列步驟也適用於公開啟動者從回應者接收回應訊息的情況。</span><span class="sxs-lookup"><span data-stu-id="26cf4-118">The following steps are also applicable for the scenario in which the public initiator receives a response message from the responder.</span></span>  
  
2.  <span data-ttu-id="26cf4-119">如果接收管線、公開程序和驗證配接器 (如果適用) 執行的驗證成功，回應者公開程序就會呼叫 `BeginNotify` 類別中的 `ApplicationAdapter` 方法。</span><span class="sxs-lookup"><span data-stu-id="26cf4-119">If validation by the receive pipeline and public process, and validation adapter, if applicable, was successful, the responder public process calls the `BeginNotify` method in the `ApplicationAdapter` class.</span></span> <span data-ttu-id="26cf4-120">這個方法會通知回應者私用程序，公開程序已經收到新的訊息，並將訊息儲存在 MessageBox 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="26cf4-120">This method notifies the responder private process that the public process has received the new message and saved the message in the MessageBox database.</span></span>  
  
3.  <span data-ttu-id="26cf4-121">回應者公開程序會傳送信號訊息給啟動者。</span><span class="sxs-lookup"><span data-stu-id="26cf4-121">The responder public process sends a signal message back to the initiator.</span></span>  
  
4.  <span data-ttu-id="26cf4-122">回應者公開程序會傳送訊息服務內容給回應者私用程序。</span><span class="sxs-lookup"><span data-stu-id="26cf4-122">The responder public process sends the message service content to the responder private process.</span></span>  
  
5.  <span data-ttu-id="26cf4-123">回應者私用程序會將訊息放在 BTARNDATA 資料庫的 MessagesToLOB 表格中。</span><span class="sxs-lookup"><span data-stu-id="26cf4-123">The responder private process puts the message in the MessagesToLOB table of the BTARNDATA database.</span></span>  
  
6.  <span data-ttu-id="26cf4-124">回應者私用程序會呼叫 `Notify` 類別中的 `ApplicationAdapter` 方法，將 End Notify 訊息傳回給回應者公開程序。</span><span class="sxs-lookup"><span data-stu-id="26cf4-124">The responder private process calls the `Notify` method in the `ApplicationAdapter` class to send the End Notify message back to the responder public process.</span></span> <span data-ttu-id="26cf4-125">回應者公開程序必須接收這個 End Notify 訊息，程序才能順利完成。</span><span class="sxs-lookup"><span data-stu-id="26cf4-125">The responder public process must receive the End Notify message for the process to be successfully completed.</span></span> <span data-ttu-id="26cf4-126">否則，訊息會處於擱置狀態。</span><span class="sxs-lookup"><span data-stu-id="26cf4-126">Otherwise, the message is suspended.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26cf4-127">您可以使用 `Notify` 訊息發出信號，告知企業營運系統 (LOB) 應用程式，此訊息正在 MessagesToLOB 表格中等候。</span><span class="sxs-lookup"><span data-stu-id="26cf4-127">You can use the `Notify` message to signal the line-of-business (LOB) application that the message is waiting in the MessagesToLOB table.</span></span> <span data-ttu-id="26cf4-128">只要系統通知 LOB 應用程式，LOB 應用程式就能從該表格接收訊息。</span><span class="sxs-lookup"><span data-stu-id="26cf4-128">As soon the system alerts the LOB application, the LOB application can retrieve the message from that table.</span></span>  
  
## <a name="to-implement-this-sample"></a><span data-ttu-id="26cf4-129">實作這個範例</span><span class="sxs-lookup"><span data-stu-id="26cf4-129">To Implement this Sample</span></span>  
 <span data-ttu-id="26cf4-130">若要實作 ApplicationAdapter 範例，您必須在協議中加入應用程式配接器。</span><span class="sxs-lookup"><span data-stu-id="26cf4-130">To implement the ApplicationAdapter sample, you must add the application adapter to the agreement.</span></span>  
  
#### <a name="to-add-the-application-adapter-to-an-agreement"></a><span data-ttu-id="26cf4-131">在協議中加入應用程式配接器</span><span class="sxs-lookup"><span data-stu-id="26cf4-131">To add the application adapter to an agreement</span></span>  
  
1. <span data-ttu-id="26cf4-132">按一下 **開始**，指向**所有程式**，指向 Microsoft **BizTalk\<版本\>Accelerator for RosettaNet**，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]**Management Console**。</span><span class="sxs-lookup"><span data-stu-id="26cf4-132">Click **Start**, point to **All Programs**, point to Microsoft **BizTalk \<version\> Accelerator for RosettaNet**, and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.</span></span>  
  
2. <span data-ttu-id="26cf4-133">在[!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)]管理主控台中，展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下**協議**。</span><span class="sxs-lookup"><span data-stu-id="26cf4-133">In the [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and click **Agreements**.</span></span>  
  
3. <span data-ttu-id="26cf4-134">按兩下您要加入至應用程式配接器的協議。</span><span class="sxs-lookup"><span data-stu-id="26cf4-134">Double-click the agreement to which you want to add the application adapter.</span></span>  
  
4. <span data-ttu-id="26cf4-135">在 **應用程式配接器**方塊中，按一下省略符號按鈕 (**...**) 按鈕右邊**組件名稱**，移至包含應用程式配接器組件的位置，選取適當的.dll 檔案，，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="26cf4-135">In the **Application Adapter** box, click the ellipsis button (**...**) button to the right of **Assembly name**, move to the location that contains the application adapter assembly, select the appropriate .dll file, and then click **Open**.</span></span>  
  
5. <span data-ttu-id="26cf4-136">按一下向下的箭號**類別名稱**，選取 應用程式配接器類別，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="26cf4-136">Click the down arrow for **Class Name**, select the application adapter class, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26cf4-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26cf4-137">See Also</span></span>  
 [<span data-ttu-id="26cf4-138">配接器範例</span><span class="sxs-lookup"><span data-stu-id="26cf4-138">Adapter Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)