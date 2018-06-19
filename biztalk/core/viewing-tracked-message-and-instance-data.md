---
title: 檢視追蹤的訊息和執行個體資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- monitoring, HAT
- HAT, about HAT
ms.assetid: e3cc7bef-90c7-4375-9f6c-7df00391132e
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 592fa5c85913a69f4536055cdd790d638b15bc32
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288214"
---
# <a name="viewing-tracked-message-and-instance-data"></a><span data-ttu-id="26fb1-102">檢視追蹤的訊息和執行個體資料</span><span class="sxs-lookup"><span data-stu-id="26fb1-102">Viewing Tracked Message and Instance Data</span></span>
<span data-ttu-id="26fb1-103">您可以使用歷程記錄和追蹤資料來協助疑難排解 BizTalk Server 應用程式。</span><span class="sxs-lookup"><span data-stu-id="26fb1-103">You can use historical and tracked data to help troubleshoot your BizTalk Server applications.</span></span> <span data-ttu-id="26fb1-104">例如，系統管理員可以使用歷程記錄和追蹤資料：</span><span class="sxs-lookup"><span data-stu-id="26fb1-104">For example, system administrators can use historical and tracked data to:</span></span>  
  
-   <span data-ttu-id="26fb1-105">檢視追蹤的訊息事件、 訊息屬性和訊息內文在訊息流程的各個階段。</span><span class="sxs-lookup"><span data-stu-id="26fb1-105">View tracked message events, message properties, and message bodies at various stages in a message’s flow.</span></span> <span data-ttu-id="26fb1-106">此資料可用於疑難排解或稽核用途。</span><span class="sxs-lookup"><span data-stu-id="26fb1-106">This data can be used for troubleshooting or auditing purposes.</span></span>  
  
-   <span data-ttu-id="26fb1-107">重新執行特定的協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="26fb1-107">Replay the execution of a specific orchestration instance.</span></span>  
  
-   <span data-ttu-id="26fb1-108">追蹤規則引發事件，以重建在稍後的事件順序的時間。</span><span class="sxs-lookup"><span data-stu-id="26fb1-108">Track rule firing events to reconstruct the sequence of events at a later point in time.</span></span>  
  
-   <span data-ttu-id="26fb1-109">藉由指定如訊息結構描述和訊息屬性/值組等準則的訊息查詢。</span><span class="sxs-lookup"><span data-stu-id="26fb1-109">Query for messages by specifying criteria such as message schema and message property/value pairs.</span></span> <span data-ttu-id="26fb1-110">藉此找出訊息之後，使用者可判斷訊息已進展至訊息流程的哪一個點。</span><span class="sxs-lookup"><span data-stu-id="26fb1-110">Having thus located the message, users can determine the point in the message flow to which the message has progressed.</span></span> <span data-ttu-id="26fb1-111">進階使用者也可以建立訊息的自訂 SQL Server 查詢。</span><span class="sxs-lookup"><span data-stu-id="26fb1-111">Advanced users can also create custom SQL Server queries for messages.</span></span>  
  
-   <span data-ttu-id="26fb1-112">搜尋封存資料庫中的封存資料。</span><span class="sxs-lookup"><span data-stu-id="26fb1-112">Search for archived data in an archived database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26fb1-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="26fb1-113">In This Section</span></span>  
  
-   [<span data-ttu-id="26fb1-114">檢查清單： 訊息及執行個體資料追蹤</span><span class="sxs-lookup"><span data-stu-id="26fb1-114">Checklist: Message and Instance Data Tracking</span></span>](../core/checklist-message-and-instance-data-tracking.md)  
  
-   [<span data-ttu-id="26fb1-115">訊息和執行個體資料追蹤的最佳作法</span><span class="sxs-lookup"><span data-stu-id="26fb1-115">Best Practices for Message and Instance Data Tracking</span></span>](../core/best-practices-for-message-and-instance-data-tracking.md)  
  
-   [<span data-ttu-id="26fb1-116">訊息與執行個體資料追蹤的安全性考量</span><span class="sxs-lookup"><span data-stu-id="26fb1-116">Security Considerations for Message and Instance Data Tracking</span></span>](../core/security-considerations-for-message-and-instance-data-tracking.md)  
  
-   [<span data-ttu-id="26fb1-117">瞭解追蹤資料</span><span class="sxs-lookup"><span data-stu-id="26fb1-117">Understanding Tracked Data</span></span>](../core/understanding-tracked-data.md)  
  
-   [<span data-ttu-id="26fb1-118">檢視歷程記錄和追蹤資料</span><span class="sxs-lookup"><span data-stu-id="26fb1-118">Viewing Historical and Tracked Data</span></span>](../core/viewing-historical-and-tracked-data.md)  
  
-   [<span data-ttu-id="26fb1-119">如何選取即時或封存資料來源</span><span class="sxs-lookup"><span data-stu-id="26fb1-119">How to Select a Live or Archived Data Source</span></span>](../core/how-to-select-a-live-or-archived-data-source.md)  
  
-   [<span data-ttu-id="26fb1-120">如何變更追蹤 QueryTimeout 值</span><span class="sxs-lookup"><span data-stu-id="26fb1-120">How to Change the Tracking QueryTimeout Value</span></span>](../core/how-to-change-the-tracking-querytimeout-value.md)  
  
-   [<span data-ttu-id="26fb1-121">如何儲存追蹤查詢</span><span class="sxs-lookup"><span data-stu-id="26fb1-121">How to Save a Tracking Query</span></span>](../core/how-to-save-a-tracking-query.md)  
  
-   [<span data-ttu-id="26fb1-122">如何開啟儲存的追蹤查詢</span><span class="sxs-lookup"><span data-stu-id="26fb1-122">How to Open a Saved Tracking Query</span></span>](../core/how-to-open-a-saved-tracking-query.md)  
  
-   [<span data-ttu-id="26fb1-123">檢視訊息流程</span><span class="sxs-lookup"><span data-stu-id="26fb1-123">Viewing Message Flow</span></span>](../core/viewing-message-flow.md)  
  
-   [<span data-ttu-id="26fb1-124">偵錯協調流程</span><span class="sxs-lookup"><span data-stu-id="26fb1-124">Debugging an Orchestration</span></span>](../core/debugging-an-orchestration.md)  
  
-   [<span data-ttu-id="26fb1-125">使用結果清單</span><span class="sxs-lookup"><span data-stu-id="26fb1-125">Working with the Results List</span></span>](../core/working-with-the-results-list.md)