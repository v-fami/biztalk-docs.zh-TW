---
title: 使用事件中樞配接器 |Microsoft Docs
description: 傳送和接收 BizTalk Server 中使用 Azure 事件中樞配接器的訊息
ms.custom: ''
ms.date: 11/16/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: MandiOhlinger
ms.author: plarsen
manager: anneta
ms.openlocfilehash: f6bccce51ad56fa1b8186347d8fddd5f4afbafbb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988775"
---
# <a name="event-hub-adapter-in-biztalk"></a><span data-ttu-id="b5c3d-103">在 BizTalk 中的事件中樞配接器</span><span class="sxs-lookup"><span data-stu-id="b5c3d-103">Event Hub adapter in BizTalk</span></span>

## <a name="overview"></a><span data-ttu-id="b5c3d-104">概觀</span><span class="sxs-lookup"><span data-stu-id="b5c3d-104">Overview</span></span>
<span data-ttu-id="b5c3d-105">**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]Feature Pack 2**，您可以傳送和接收 BizTalk Server 和 Azure 事件中樞之間的訊息。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-105">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 2**, you can send and receive messages between BizTalk Server and Azure Event Hubs.</span></span> 

<span data-ttu-id="b5c3d-106">Azure 事件中樞是可高度擴充的資料串流平台，並可接收和處理數百萬個每秒的事件。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-106">Azure Event Hubs is a highly scalable data streaming platform, and can receive and process millions of events per second.</span></span> <span data-ttu-id="b5c3d-107">[事件中樞是什麼？](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)提供更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-107">[What is Event Hubs?](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs) provides more details.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b5c3d-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="b5c3d-108">Prerequisites</span></span>

* <span data-ttu-id="b5c3d-109">建立[Azure 事件中樞命名空間和事件中樞](https://docs.microsoft.com/azure/event-hubs/event-hubs-create)</span><span class="sxs-lookup"><span data-stu-id="b5c3d-109">Create an [Azure event hubs namespace and event hub](https://docs.microsoft.com/azure/event-hubs/event-hubs-create)</span></span>
* <span data-ttu-id="b5c3d-110">建立[與容器的 Azure blob 儲存體帳戶](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account)</span><span class="sxs-lookup"><span data-stu-id="b5c3d-110">Create an [Azure blob storage account with a container](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account)</span></span>
* <span data-ttu-id="b5c3d-111">安裝[Feature Pack 2](https://aka.ms/bts2016fp2) BizTalk 伺服器上</span><span class="sxs-lookup"><span data-stu-id="b5c3d-111">Install [Feature Pack 2](https://aka.ms/bts2016fp2) on your BizTalk Server</span></span>

<span data-ttu-id="b5c3d-112">現已建立事件中樞，並已傳送和接收事件所需的連接字串。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-112">Your event hub is now created, and you have the connection strings you need to send and receive events.</span></span>

## <a name="send-messages-to-event-hubs"></a><span data-ttu-id="b5c3d-113">將訊息傳送至事件中樞</span><span class="sxs-lookup"><span data-stu-id="b5c3d-113">Send messages to Event Hubs</span></span>

1.  <span data-ttu-id="b5c3d-114">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，選取**新增**，然後選取**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-114">In the BizTalk Server Administration console, right-click **Send Ports**, select **New**, and select **Static One-way send port**.</span></span>

    <span data-ttu-id="b5c3d-115">[建立傳送埠](../core/how-to-create-a-send-port2.md)提供一些指引。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-115">[Create a Send Port](../core/how-to-create-a-send-port2.md) provides some guidance.</span></span>

2. <span data-ttu-id="b5c3d-116">請輸入**名稱**。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-116">Enter a **Name**.</span></span> <span data-ttu-id="b5c3d-117">在**傳輸**，將**型別**來**EventHub**，然後選取**設定**。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-117">In **Transport**, set the **Type** to **EventHub**, and select **Configure**.</span></span> 

3. <span data-ttu-id="b5c3d-118">設定**Azure 帳戶**屬性：</span><span class="sxs-lookup"><span data-stu-id="b5c3d-118">Configure the **Azure Account** properties:</span></span> 

    |<span data-ttu-id="b5c3d-119">使用</span><span class="sxs-lookup"><span data-stu-id="b5c3d-119">Use this</span></span>|<span data-ttu-id="b5c3d-120">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="b5c3d-120">To do this</span></span>|  
    |---|---|  
    | <span data-ttu-id="b5c3d-121">**登入**</span><span class="sxs-lookup"><span data-stu-id="b5c3d-121">**Sign-in**</span></span> | <span data-ttu-id="b5c3d-122">登入您的 Azure 帳戶</span><span class="sxs-lookup"><span data-stu-id="b5c3d-122">Sign into your Azure account</span></span> |
    | <span data-ttu-id="b5c3d-123">**訂閱**</span><span class="sxs-lookup"><span data-stu-id="b5c3d-123">**Subscription**</span></span> | <span data-ttu-id="b5c3d-124">選取具有您 EventHubs 命名空間的訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="b5c3d-124">Select the subscription that has your EventHubs namespace</span></span> |
    | <span data-ttu-id="b5c3d-125">**資源群組**</span><span class="sxs-lookup"><span data-stu-id="b5c3d-125">**Resource Group**</span></span> | <span data-ttu-id="b5c3d-126">選取您已將 EventHubs 命名空間的資源群組</span><span class="sxs-lookup"><span data-stu-id="b5c3d-126">Select your resource group that has your EventHubs namespace</span></span> |

4. <span data-ttu-id="b5c3d-127">設定**端點**屬性：</span><span class="sxs-lookup"><span data-stu-id="b5c3d-127">Configure the **Endpoint** properties:</span></span> 

    |<span data-ttu-id="b5c3d-128">使用</span><span class="sxs-lookup"><span data-stu-id="b5c3d-128">Use this</span></span>|<span data-ttu-id="b5c3d-129">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="b5c3d-129">To do this</span></span>|  
    |---|---|  
    | <span data-ttu-id="b5c3d-130">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="b5c3d-130">**Namespace**</span></span> | <span data-ttu-id="b5c3d-131">選取事件中樞命名空間，也就是類似 sb: / /*youreventhubnamespace*.servicebus.windows.net/</span><span class="sxs-lookup"><span data-stu-id="b5c3d-131">Select your Event Hubs namespace, which is something like sb://*youreventhubnamespace*.servicebus.windows.net/</span></span> |
    | <span data-ttu-id="b5c3d-132">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b5c3d-132">**Name**</span></span> | <span data-ttu-id="b5c3d-133">選取事件中樞 （這建立事件中樞命名空間內） 的名稱</span><span class="sxs-lookup"><span data-stu-id="b5c3d-133">Select the name of your Event Hub (which was created within your Event Hubs namespace)</span></span> |
    | <span data-ttu-id="b5c3d-134">**預設資料分割索引鍵**</span><span class="sxs-lookup"><span data-stu-id="b5c3d-134">**Default Partition Key**</span></span> | <span data-ttu-id="b5c3d-135">選擇性。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-135">Optional.</span></span> <span data-ttu-id="b5c3d-136">[事件中樞程式設計指南](https://docs.microsoft.com/azure/event-hubs/event-hubs-programming-guide)此金鑰提供更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-136">[Event Hubs programming guide](https://docs.microsoft.com/azure/event-hubs/event-hubs-programming-guide) provides more details on this key.</span></span> |
    | <span data-ttu-id="b5c3d-137">**驗證**</span><span class="sxs-lookup"><span data-stu-id="b5c3d-137">**Authentication**</span></span> | <span data-ttu-id="b5c3d-138">**命名空間存取簽章**是預設值，並會自動使用 [RootManageSharedAccessKey] 時建立事件中樞命名空間所建立。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-138">**Namespace Access Signature** is the default, and automatically uses the RootManageSharedAccessKey that's created when you create an Event Hubs namespace.</span></span><br/><br/><span data-ttu-id="b5c3d-139">**實體存取簽章**是在事件中樞層級 （非事件中樞命名空間層級），您可以建立 SAS 原則。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-139">**Entity Access Signature** is the SAS policy you can create at the Event Hub-level (not the Event Hubs namespace-level).</span></span> <br/><br/><span data-ttu-id="b5c3d-140">[事件中樞功能概觀](https://docs.microsoft.com/azure/event-hubs/event-hubs-features)說明更多。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-140">[Event Hubs features overview](https://docs.microsoft.com/azure/event-hubs/event-hubs-features) explains more.</span></span> |

    <span data-ttu-id="b5c3d-141">完成時，您的屬性看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="b5c3d-141">When finished, your properties look similar to the following:</span></span> 

    ![端點屬性](../core/media/event-hub-endpoint-properties.png)


5. <span data-ttu-id="b5c3d-143">選擇性。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-143">Optional.</span></span> <span data-ttu-id="b5c3d-144">設定**訊息**屬性。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-144">Configure the **Message** properties.</span></span> <span data-ttu-id="b5c3d-145">**使用者定義的訊息屬性的命名空間**值代表 BizTalk 訊息的結構描述，對應至事件中樞的訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-145">The **Namespace for User Defined Message Properties** value represents a BizTalk message schema mapped to Event Hubs message properties.</span></span>

6. <span data-ttu-id="b5c3d-146">選取  **Ok**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-146">Select **Ok** to save your changes.</span></span> 


### <a name="test-your-send-port"></a><span data-ttu-id="b5c3d-147">測試您的傳送埠</span><span class="sxs-lookup"><span data-stu-id="b5c3d-147">Test your send port</span></span>

<span data-ttu-id="b5c3d-148">您可以使用簡單檔案接收埠，並將訊息傳送至您的 Azure 事件中樞的位置。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-148">You can use a simple File receive port and location to send messages to your Azure Event Hub.</span></span> 

1. <span data-ttu-id="b5c3d-149">建立使用 File 配接器的接收埠。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-149">Create a receive port using the File adapter.</span></span> <span data-ttu-id="b5c3d-150">內您接收位置，設定**接收資料夾**要**C:\Temp\In\\**，並將檔案遮罩設定為 **\*.xml**。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-150">Within your receive location,  set the **Receive folder** to **C:\Temp\In\\**, and set the file mask to **\*.xml**.</span></span>
2. <span data-ttu-id="b5c3d-151">在事件中樞將傳送埠屬性，設定**篩選條件**至`BTS.ReceivePortName == FileReceivePort`。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-151">In your Event Hub send port properties, set the **Filters** to `BTS.ReceivePortName == FileReceivePort`.</span></span>
3. <span data-ttu-id="b5c3d-152">將下列內容貼入文字編輯器，並將檔案儲存為**EventHubMessage.xml**。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-152">Paste the following into a text editor, and save the file as **EventHubMessage.xml**.</span></span> <span data-ttu-id="b5c3d-153">這是您的範例訊息。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-153">This is your sample message.</span></span> 

    ```xml
    <Data>
      <DataID>DataID_0</DataID>
      <DataDetails>DataDetails_0</DataDetails>
    </Data>
    ```

4. <span data-ttu-id="b5c3d-154">啟動檔案接收位置和事件中樞傳送埠。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-154">Start the File receive location and the Event Hub send port.</span></span>
5. <span data-ttu-id="b5c3d-155">複製**EventHubMessage.xml**範例訊息至接收資料夾 (C:\Temp\In\)。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-155">Copy **EventHubMessage.xml** sample message into the receive folder (C:\Temp\In\).</span></span> <span data-ttu-id="b5c3d-156">傳送埠會將 XML 檔案傳送到事件中樞。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-156">The send port sends the XML file to the event hub.</span></span>

## <a name="receive-messages-from-event-hubs"></a><span data-ttu-id="b5c3d-157">從事件中樞接收訊息</span><span class="sxs-lookup"><span data-stu-id="b5c3d-157">Receive messages from Event Hubs</span></span>

1. <span data-ttu-id="b5c3d-158">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**接收連接埠**，選取**新增**，然後選取**單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-158">In the BizTalk Server Administration console, right-click **Receive Ports**, select **New**, and select **One-Way receive port**.</span></span> 

    <span data-ttu-id="b5c3d-159">[建立接收埠](../core/how-to-create-a-receive-port.md)提供一些指引。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-159">[Create a receive port](../core/how-to-create-a-receive-port.md) provides some guidance.</span></span>

2. <span data-ttu-id="b5c3d-160">輸入名稱，然後選取**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-160">Enter a name, and select **Receive Locations**.</span></span> 

3. <span data-ttu-id="b5c3d-161">選取 **的新**，並**名稱**接收位置。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-161">Select **New**, and **Name** the receive location.</span></span> <span data-ttu-id="b5c3d-162">在 **傳輸**，選取**EventHub**從**型別**下拉式清單，然後選取**設定**。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-162">In **Transport**, select **EventHub** from the **Type** drop-down list, and then select **Configure**.</span></span> 

4. <span data-ttu-id="b5c3d-163">設定**Azure 帳戶**屬性：</span><span class="sxs-lookup"><span data-stu-id="b5c3d-163">Configure the **Azure Account** properties:</span></span> 

    |<span data-ttu-id="b5c3d-164">使用</span><span class="sxs-lookup"><span data-stu-id="b5c3d-164">Use this</span></span>|<span data-ttu-id="b5c3d-165">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="b5c3d-165">To do this</span></span>|  
    |---|---|  
    | <span data-ttu-id="b5c3d-166">**登入**</span><span class="sxs-lookup"><span data-stu-id="b5c3d-166">**Sign-in**</span></span> | <span data-ttu-id="b5c3d-167">登入您的 Azure 帳戶</span><span class="sxs-lookup"><span data-stu-id="b5c3d-167">Sign into your Azure account</span></span> |
    | <span data-ttu-id="b5c3d-168">**訂閱**</span><span class="sxs-lookup"><span data-stu-id="b5c3d-168">**Subscription**</span></span> | <span data-ttu-id="b5c3d-169">選取具有您 EventHubs 命名空間的訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="b5c3d-169">Select the subscription that has your EventHubs namespace</span></span> |
    | <span data-ttu-id="b5c3d-170">**資源群組**</span><span class="sxs-lookup"><span data-stu-id="b5c3d-170">**Resource Group**</span></span> | <span data-ttu-id="b5c3d-171">選取您已將 EventHubs 命名空間的資源群組</span><span class="sxs-lookup"><span data-stu-id="b5c3d-171">Select your resource group that has your EventHubs namespace</span></span> |

4. <span data-ttu-id="b5c3d-172">設定**端點**屬性：</span><span class="sxs-lookup"><span data-stu-id="b5c3d-172">Configure the **Endpoint** properties:</span></span> 

    |<span data-ttu-id="b5c3d-173">使用</span><span class="sxs-lookup"><span data-stu-id="b5c3d-173">Use this</span></span>|<span data-ttu-id="b5c3d-174">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="b5c3d-174">To do this</span></span>|  
    |---|---|  
    | <span data-ttu-id="b5c3d-175">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="b5c3d-175">**Namespace**</span></span> | <span data-ttu-id="b5c3d-176">選取事件中樞命名空間，也就是類似 sb: / /*youreventhubnamespace*.servicebus.windows.net/</span><span class="sxs-lookup"><span data-stu-id="b5c3d-176">Select your Event Hubs namespace, which is something like sb://*youreventhubnamespace*.servicebus.windows.net/</span></span> |
    | <span data-ttu-id="b5c3d-177">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b5c3d-177">**Name**</span></span> | <span data-ttu-id="b5c3d-178">選取事件中樞 （這建立事件中樞命名空間內） 的名稱</span><span class="sxs-lookup"><span data-stu-id="b5c3d-178">Select the name of your Event Hub (which was created within your Event Hubs namespace)</span></span> |
    | <span data-ttu-id="b5c3d-179">**取用者群組**</span><span class="sxs-lookup"><span data-stu-id="b5c3d-179">**Consumer Group**</span></span> | <span data-ttu-id="b5c3d-180">選取事件中樞內的取用者群組。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-180">Select the Consumer group within your Event Hub.</span></span> <span data-ttu-id="b5c3d-181">會自動建立預設群組。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-181">A default group is created automatically.</span></span> <br/><br/><span data-ttu-id="b5c3d-182">[事件中樞功能概觀](https://docs.microsoft.com/azure/event-hubs/event-hubs-features)提供更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-182">[Event Hubs features overview](https://docs.microsoft.com/azure/event-hubs/event-hubs-features) provides more details.</span></span> |
    | <span data-ttu-id="b5c3d-183">**驗證**</span><span class="sxs-lookup"><span data-stu-id="b5c3d-183">**Authentication**</span></span> | <span data-ttu-id="b5c3d-184">**命名空間存取簽章**是預設值，並會自動使用 [RootManageSharedAccessKey] 時建立事件中樞命名空間所建立。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-184">**Namespace Access Signature** is the default, and automatically uses the RootManageSharedAccessKey that's created when you create an Event Hubs namespace.</span></span><br/><br/><span data-ttu-id="b5c3d-185">**實體存取簽章**是在事件中樞層級 （非事件中樞命名空間層級），您可以建立 SAS 原則。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-185">**Entity Access Signature** is the SAS policy you can create at the Event Hub-level (not the Event Hubs namespace-level).</span></span> <br/><br/><span data-ttu-id="b5c3d-186">[事件中樞功能概觀](https://docs.microsoft.com/azure/event-hubs/event-hubs-features)說明更多。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-186">[Event Hubs features overview](https://docs.microsoft.com/azure/event-hubs/event-hubs-features) explains more.</span></span> |

    <span data-ttu-id="b5c3d-187">完成時，您的屬性看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="b5c3d-187">When finished, your properties look similar to the following:</span></span> 

    ![端點屬性](../core/media/event-hub-endpoint-receive-properties.png)

5. <span data-ttu-id="b5c3d-189">設定**檢查點**屬性。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-189">Configure the **Checkpoint** properties.</span></span> <span data-ttu-id="b5c3d-190">此配接器會使用 Azure blob 儲存體帳戶，可靠地讀取事件使用檢查點，然後再繼續重新啟動。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-190">This adapter uses an Azure blob storage account to reliably read events using a checkpoint, and resume from a restart.</span></span> 

    <span data-ttu-id="b5c3d-191">**存放裝置驗證** </span><span class="sxs-lookup"><span data-stu-id="b5c3d-191">**Storage Authentication** </span></span>  
    <span data-ttu-id="b5c3d-192">選取驗證方法。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-192">Select an authentication method.</span></span> <span data-ttu-id="b5c3d-193">一般而言，建議使用共用存取簽章。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-193">Typically, it's recommended to use a Shared Access Signature.</span></span> <span data-ttu-id="b5c3d-194">下列連結是不錯的資源，可協助您決定何者最適合您的案例：</span><span class="sxs-lookup"><span data-stu-id="b5c3d-194">The following links are good resources to help you decide which is right for your scenario:</span></span><br/><br/>[<span data-ttu-id="b5c3d-195">關於 Azure 儲存體帳戶</span><span class="sxs-lookup"><span data-stu-id="b5c3d-195">About Azure storage accounts</span></span>](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account)<br/>[<span data-ttu-id="b5c3d-196">使用共用的存取簽章 (SAS)</span><span class="sxs-lookup"><span data-stu-id="b5c3d-196">Using shared access signatures (SAS)</span></span>](https://docs.microsoft.com/azure/storage/common/storage-dotnet-shared-access-signature-part-1)

    <span data-ttu-id="b5c3d-197">完成時，您的屬性看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="b5c3d-197">When finished, your properties look similar to the following:</span></span> 

    ![檢查點內容](../core/media/event-hub-receive-checkpoint.png)

6. <span data-ttu-id="b5c3d-199">設定**訊息**屬性：</span><span class="sxs-lookup"><span data-stu-id="b5c3d-199">Configure the **Message** properties:</span></span> 

    |<span data-ttu-id="b5c3d-200">使用</span><span class="sxs-lookup"><span data-stu-id="b5c3d-200">Use this</span></span>|<span data-ttu-id="b5c3d-201">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="b5c3d-201">To do this</span></span>|  
    |---|---|  
    | <span data-ttu-id="b5c3d-202">**命名空間，使用者定義訊息屬性**</span><span class="sxs-lookup"><span data-stu-id="b5c3d-202">**Namespace for User Defined Message Properties**</span></span> | <span data-ttu-id="b5c3d-203"> http://schemas.microsoft.com/BizTalk/EventHubAdapter/EventData/User 預設結構描述中，但您可以輸入另一個結構描述。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-203">http://schemas.microsoft.com/BizTalk/EventHubAdapter/EventData/User is the default schema, but you can enter another schema.</span></span> <span data-ttu-id="b5c3d-204">這個值代表 BizTalk 訊息的結構描述，對應至事件中樞的訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-204">This value represents a BizTalk message schema mapped to Event Hubs message properties.</span></span> |
    | <span data-ttu-id="b5c3d-205">**升級使用者定義的屬性**</span><span class="sxs-lookup"><span data-stu-id="b5c3d-205">**Promote user defined properties**</span></span> | <span data-ttu-id="b5c3d-206">選擇性。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-206">Optional.</span></span> <span data-ttu-id="b5c3d-207">如果您想，您可以升級這些屬性。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-207">You can promote these properties if you prefer.</span></span> <br/><br/><span data-ttu-id="b5c3d-208">**注意**</span><span class="sxs-lookup"><span data-stu-id="b5c3d-208">**NOTE**</span></span><br/><span data-ttu-id="b5c3d-209">要升級的屬性應該部署的 porperty 結構描述*之前*接收事件。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-209">The properties that need to be promoted should have a porperty schema deployed *before* receiving events.</span></span>|

7. <span data-ttu-id="b5c3d-210">選取  **Ok**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-210">Select **Ok** to save your changes.</span></span> 

### <a name="test-your-receive-settings"></a><span data-ttu-id="b5c3d-211">測試您接收設定</span><span class="sxs-lookup"><span data-stu-id="b5c3d-211">Test your receive settings</span></span>

<span data-ttu-id="b5c3d-212">您可以使用簡單的 File 傳送埠以接收來自 Azure 事件中樞的訊息。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-212">You can use a simple File send port to receive messages from your Azure Event Hub.</span></span> 

1. <span data-ttu-id="b5c3d-213">建立使用 File 配接器的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-213">Create a send port using the File adapter.</span></span> <span data-ttu-id="b5c3d-214">在您傳送連接埠的屬性，設定**目的地資料夾**要**C:\Temp\Out\\**，並設定和**檔案名稱**至 **%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="b5c3d-214">Within your send port properties, set the **Destination folder** to **C:\Temp\Out\\**, and set the and **File name** to **%MessageID%.xml**.</span></span>
2. <span data-ttu-id="b5c3d-215">在您的檔案傳送埠屬性，設定**篩選條件**至`BTS.ReceivePortName == EHReceivePort`。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-215">In your File send port properties, set the **Filters** to  `BTS.ReceivePortName == EHReceivePort`.</span></span>
3. <span data-ttu-id="b5c3d-216">開始事件中樞接收位置和 File 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-216">Start the Event Hub receive location and the File send port.</span></span>
4. <span data-ttu-id="b5c3d-217">尋找目的地資料夾 (c:\temp\out) 中的訊息。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-217">Look for messages in the destination folder (c:\temp\out).</span></span>

## <a name="do-more"></a><span data-ttu-id="b5c3d-218">執行更多作業</span><span class="sxs-lookup"><span data-stu-id="b5c3d-218">Do more</span></span>
<span data-ttu-id="b5c3d-219">事件中樞會被視為 「 前端 」 許多其他 Azure 服務，包括 Azure Data Lake、 HD Insight 和更多功能。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-219">Event Hubs is considered the "front door" to a lot of other Azure services, including Azure Data Lake, HD Insight, and more.</span></span> <span data-ttu-id="b5c3d-220">它被設計來處理許多訊息，並加以處理快速。</span><span class="sxs-lookup"><span data-stu-id="b5c3d-220">It's designed to process a lot of messages, and process them fast.</span></span> <span data-ttu-id="b5c3d-221">深入的了解事件中樞，以及其功能：</span><span class="sxs-lookup"><span data-stu-id="b5c3d-221">Read more about Event Hubs, and its features:</span></span> 

[<span data-ttu-id="b5c3d-222">事件中樞功能概觀</span><span class="sxs-lookup"><span data-stu-id="b5c3d-222">Event Hubs features overview</span></span>](https://docs.microsoft.com/azure/event-hubs/event-hubs-features)  
[<span data-ttu-id="b5c3d-223">事件中樞是什麼？</span><span class="sxs-lookup"><span data-stu-id="b5c3d-223">What is Event Hubs?</span></span>](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)