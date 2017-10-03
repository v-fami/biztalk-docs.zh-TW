---
title: "建立 RFC，SAP 使用 SAP 配接器在 BizTalk 中的概觀 |Microsoft 文件"
description: "建立 RFC，RFC 目的地，並將傳送到從 SAP 系統-BizTalk 配接器組件 (BAP) 的 RFC"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35937183-fc1e-49cd-8a75-8f62effe0013
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 802a2e33b8bc902dc784276ce7c1d9c3f37f3b12
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="create-and-send-an-rfc-in-sap"></a><span data-ttu-id="e866d-103">建立並傳送 sap RFC</span><span class="sxs-lookup"><span data-stu-id="e866d-103">Create and send an RFC in SAP</span></span>
<span data-ttu-id="e866d-104">列出為了建立 RFC SAP 系統上完成的高階工作。</span><span class="sxs-lookup"><span data-stu-id="e866d-104">Lists high-level tasks to complete on the SAP system to create an RFC.</span></span> <span data-ttu-id="e866d-105">每個工作可能會非常詳細的程序。</span><span class="sxs-lookup"><span data-stu-id="e866d-105">Each task may involve very detailed procedures.</span></span> <span data-ttu-id="e866d-106">如此一來，我們建議連絡您的 SAP 系統管理員，以完成這些工作，或請參閱 SAP 指引。</span><span class="sxs-lookup"><span data-stu-id="e866d-106">As a result, we recommend contacting your SAP administrator to complete these tasks, or refer to the SAP guidance.</span></span>  
  
## <a name="create-an-rfc"></a><span data-ttu-id="e866d-107">建立 RFC</span><span class="sxs-lookup"><span data-stu-id="e866d-107">Create an RFC</span></span>  
  
1.  <span data-ttu-id="e866d-108">啟動 SAP GUI。</span><span class="sxs-lookup"><span data-stu-id="e866d-108">Start the SAP GUI.</span></span>  
  
2.  <span data-ttu-id="e866d-109">移至交易 SE37 （函式產生器），輸入 RFC 名稱，然後按一下**建立**。</span><span class="sxs-lookup"><span data-stu-id="e866d-109">Go to Transaction SE37 (Function Builder), enter the RFC name, and click **Create**.</span></span>  
  
3.  <span data-ttu-id="e866d-110">輸入現有函式群組在其下將會建立 RFC，RFC 的簡短描述，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="e866d-110">Enter an existing function group under which the RFC will be created, a short description for the RFC, and click **Save**.</span></span>  
  
4.  <span data-ttu-id="e866d-111">在**屬性**索引標籤上，選取**Remote-Enabled 模組**選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="e866d-111">In the **Attributes** tab, select the **Remote-Enabled Module** radio button.</span></span>  
  
5.  <span data-ttu-id="e866d-112">在**匯入**索引標籤上，輸入匯入參數。</span><span class="sxs-lookup"><span data-stu-id="e866d-112">In the **Import** tab, enter the import parameters.</span></span> <span data-ttu-id="e866d-113">這些參數可用來將外部資料傳遞至函式模組。</span><span class="sxs-lookup"><span data-stu-id="e866d-113">These parameters are used for passing the external data to the function module.</span></span>  
  
6.  <span data-ttu-id="e866d-114">在**匯出**索引標籤上，輸入匯出的參數。</span><span class="sxs-lookup"><span data-stu-id="e866d-114">In the **Export** tab, enter the export parameters.</span></span>  
  
7.  <span data-ttu-id="e866d-115">在**變更**索引標籤上，輸入變更的參數。</span><span class="sxs-lookup"><span data-stu-id="e866d-115">In the **Changing** tab, enter the changing parameters.</span></span>  
  
8.  <span data-ttu-id="e866d-116">在**資料表**索引標籤上，輸入資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="e866d-116">In the **Tables** tab, enter the table names.</span></span>  
  
9. <span data-ttu-id="e866d-117">在**例外狀況**索引標籤上，輸入來處理錯誤的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e866d-117">In the **Exceptions** tab, enter the exceptions to handle errors.</span></span>  
  
10. <span data-ttu-id="e866d-118">在**原始程式碼**索引標籤上，輸入原始碼 （邏輯） 的 RFC。</span><span class="sxs-lookup"><span data-stu-id="e866d-118">In the **Source Code** tab, enter the source code (logic) for the RFC.</span></span>  
  
11. <span data-ttu-id="e866d-119">按一下**Activate**啟動函式模組 工具列上的圖示。</span><span class="sxs-lookup"><span data-stu-id="e866d-119">Click the **Activate** icon on the toolbar to activate the function module.</span></span>  

## <a name="create-an-rfc-destination"></a><span data-ttu-id="e866d-120">建立 RFC 目的地</span><span class="sxs-lookup"><span data-stu-id="e866d-120">Create an RFC destination</span></span>  
  
1.  <span data-ttu-id="e866d-121">啟動 SAP GUI。</span><span class="sxs-lookup"><span data-stu-id="e866d-121">Start the SAP GUI.</span></span>  
  
2.  <span data-ttu-id="e866d-122">移至交易 SM59 （顯示和維護 RFC 目的地）。</span><span class="sxs-lookup"><span data-stu-id="e866d-122">Go to Transaction SM59 (Display and Maintain RFC Destinations).</span></span>  
  
3.  <span data-ttu-id="e866d-123">從功能表列中，按一下 **建立**。</span><span class="sxs-lookup"><span data-stu-id="e866d-123">From the menu bar, click **Create**.</span></span>  
  
4.  <span data-ttu-id="e866d-124">輸入的 RFC 目的地、 連接類型、 描述，然後按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="e866d-124">Enter the RFC destination, connection type, description, and then press Enter.</span></span>  
  
5.  <span data-ttu-id="e866d-125">選取**已註冊的伺服器程式**選項按鈕，輸入程式識別碼、 閘道器主機和閘道服務。</span><span class="sxs-lookup"><span data-stu-id="e866d-125">Select the **Registered Server Program** radio-button, enter the program ID, gateway host, and gateway service.</span></span>  
  
6.  <span data-ttu-id="e866d-126">儲存 RFC 目的地。</span><span class="sxs-lookup"><span data-stu-id="e866d-126">Save the RFC destination.</span></span>  

## <a name="send-an-rfc-from-an-sap-system"></a><span data-ttu-id="e866d-127">從 SAP 系統傳送的 RFC</span><span class="sxs-lookup"><span data-stu-id="e866d-127">Send an RFC from an SAP system</span></span>  
  
1.  <span data-ttu-id="e866d-128">啟動 SAP GUI。</span><span class="sxs-lookup"><span data-stu-id="e866d-128">Start the SAP GUI.</span></span>  
  
2.  <span data-ttu-id="e866d-129">建立使用 BD54 交易的邏輯系統。</span><span class="sxs-lookup"><span data-stu-id="e866d-129">Create a logical system using BD54 transaction.</span></span>  
  
3.  <span data-ttu-id="e866d-130">在 TCP/IP 連線使用 SM59 交易建立 RFC 目的地。</span><span class="sxs-lookup"><span data-stu-id="e866d-130">Create an RFC destination in TCP/IP connections using SM59 transaction.</span></span>  
  
4.  <span data-ttu-id="e866d-131">建立使用 WE21 交易的連接埠，並將它附加到最後一個步驟中建立的 RFC 目的地。</span><span class="sxs-lookup"><span data-stu-id="e866d-131">Create a port using WE21 transaction and attach it to the RFC destination created in the last step.</span></span>  
  
5.  <span data-ttu-id="e866d-132">使用 SE37 觸發 RFC。</span><span class="sxs-lookup"><span data-stu-id="e866d-132">Trigger an RFC by using SE37.</span></span> <span data-ttu-id="e866d-133">這個 RFC 必須包含邏輯，以進行 RFC 呼叫外部應用程式，然後在該應用程式中收到的回應。</span><span class="sxs-lookup"><span data-stu-id="e866d-133">This RFC must contain the logic to make an RFC call to an external application and then receive a response from that application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e866d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e866d-134">See Also</span></span>  
 [<span data-ttu-id="e866d-135">使用特定 SAP 配接器實例的 SAP GUI 執行工作</span><span class="sxs-lookup"><span data-stu-id="e866d-135">Performing Tasks Using the SAP GUI for Specific SAP Adapter Scenarios</span></span>](performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)