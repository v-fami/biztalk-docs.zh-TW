---
title: "從 SAP 系統在 BizTalk 中使用 mySAP 配接器傳送 Idoc |Microsoft 文件"
description: 
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aea8a5e9-d775-4d52-a434-c2908b53cd2d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63f7d1ccdaa8cb6a4ee12ad1cc4263c487a164c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sending-idocs-from-an-sap-system"></a><span data-ttu-id="250f9-102">從 SAP 系統傳送 Idoc</span><span class="sxs-lookup"><span data-stu-id="250f9-102">Sending IDOCs from an SAP System</span></span>
<span data-ttu-id="250f9-103">SAP 系統從 SAP 系統傳送 IDOC 至外部應用程式上完成的高階工作。</span><span class="sxs-lookup"><span data-stu-id="250f9-103">High-level tasks to complete on the SAP system to send an IDOC from the SAP system to an external application.</span></span> <span data-ttu-id="250f9-104">連絡您的 SAP 系統管理員執行這些工作，或請參閱 SAP 指引。</span><span class="sxs-lookup"><span data-stu-id="250f9-104">Contact your SAP administrator for performing these tasks or see the SAP guidance.</span></span>  
  
## <a name="send-an-idoc-from-sap"></a><span data-ttu-id="250f9-105">從 SAP 傳送 IDOC</span><span class="sxs-lookup"><span data-stu-id="250f9-105">Send an IDOC from SAP</span></span>  
  
1.  <span data-ttu-id="250f9-106">啟動 SAP GUI。</span><span class="sxs-lookup"><span data-stu-id="250f9-106">Start the SAP GUI.</span></span>  
  
2.  <span data-ttu-id="250f9-107">建立使用 BD54 交易的邏輯系統。</span><span class="sxs-lookup"><span data-stu-id="250f9-107">Create a logical system using BD54 transaction.</span></span>  
  
3.  <span data-ttu-id="250f9-108">在 TCP/IP 連線使用 SM59 交易建立 RFC 目的地。</span><span class="sxs-lookup"><span data-stu-id="250f9-108">Create an RFC destination in TCP/IP connections using SM59 transaction.</span></span>  
  
4.  <span data-ttu-id="250f9-109">建立使用 WE21 交易的連接埠，並將它附加到最後一個步驟中建立的 RFC 目的地。</span><span class="sxs-lookup"><span data-stu-id="250f9-109">Create a port using WE21 transaction and attach it to the RFC destination created in the last step.</span></span>  
  
5.  <span data-ttu-id="250f9-110">建立具有必要的訊息類型和 IDOC 類型使用 WE20 交易夥伴設定檔，並將其附加到最後一個步驟中建立的連接埠。</span><span class="sxs-lookup"><span data-stu-id="250f9-110">Create a partner profile using WE20 transaction with the required message type and IDOC type, and then attach it to the port created in the last step.</span></span>  
  
6.  <span data-ttu-id="250f9-111">連接至使用銷售交易的連接埠的訊息類型，藉此維持分散式的模型。</span><span class="sxs-lookup"><span data-stu-id="250f9-111">Maintain a distributed model by connecting the message type to the port using the SALE transaction.</span></span>  
  
7.  <span data-ttu-id="250f9-112">產生內 SAP IDOC。</span><span class="sxs-lookup"><span data-stu-id="250f9-112">Generate an IDOC within SAP.</span></span> <span data-ttu-id="250f9-113">例如，使用 BD10 交易來觸發 MATMAS IDOC。</span><span class="sxs-lookup"><span data-stu-id="250f9-113">For example, use BD10 transaction to trigger a MATMAS IDOC.</span></span> <span data-ttu-id="250f9-114">如需有關其他觸發程序特定的 Idoc 的交易資訊，請連絡 SAP 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="250f9-114">Contact your SAP administrator for information about other transactions to trigger specific IDOCs.</span></span>  

## <a name="view-transaction-ids-in-sap"></a><span data-ttu-id="250f9-115">檢視 SAP 中的交易識別碼</span><span class="sxs-lookup"><span data-stu-id="250f9-115">View Transaction IDs in SAP</span></span>
<span data-ttu-id="250f9-116">當[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]tRFC 會叫用，或傳送 IDOC 到 SAP 系統，SAP 系統暫存器的交易識別碼 (TID) 回應。</span><span class="sxs-lookup"><span data-stu-id="250f9-116">When the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] invokes a tRFC or sends an IDOC to an SAP system, the SAP system registers a transaction ID (TID) in response.</span></span> <span data-ttu-id="250f9-117">在某些情況下，您可能需要知道已向 SAP 系統，以回應從呼叫 TID [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="250f9-117">In some scenarios, you might need to know the TID that is registered with the SAP system in response to a call from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="250f9-118">例如，您可以疑難排解問題的 SAP 系統上識別工作 (LUW) 的邏輯單元。</span><span class="sxs-lookup"><span data-stu-id="250f9-118">For example, you might want to identify the logical unit of work (LUW) on the SAP system to troubleshoot an issue.</span></span>  
  
 <span data-ttu-id="250f9-119">若要檢視 TIDs SAP 系統中，您必須使用 SM58 交易。</span><span class="sxs-lookup"><span data-stu-id="250f9-119">To view the TIDs in an SAP system, you must use transaction SM58.</span></span> <span data-ttu-id="250f9-120">請連絡您的 SAP 系統管理員，或請參閱 SAP 指引，如需有關此交易。</span><span class="sxs-lookup"><span data-stu-id="250f9-120">Contact your SAP administrator or refer to the SAP guidance for more information about this transaction.</span></span> 

## <a name="view-details-about-idocs-sent-and-received-from-sap"></a><span data-ttu-id="250f9-121">檢視傳送和從 SAP 接收 Idoc 的詳細資料</span><span class="sxs-lookup"><span data-stu-id="250f9-121">View details about IDOCs sent and received from SAP</span></span>
<span data-ttu-id="250f9-122">使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，您可以傳送 IDOC 至 SAP 系統，或從 SAP 系統接收 IDOC。</span><span class="sxs-lookup"><span data-stu-id="250f9-122">Using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you can send an IDOC to an SAP system or receive an IDOC from an SAP system.</span></span> <span data-ttu-id="250f9-123">若要追蹤的 SAP 系統的狀態和傳送或接收的 IDOC 資料的檢視，您可以使用 WE02 交易。</span><span class="sxs-lookup"><span data-stu-id="250f9-123">To track the status and view the data of an IDOC sent or received by an SAP system, you can use transaction WE02.</span></span> <span data-ttu-id="250f9-124">請連絡您的 SAP 系統管理員，或參閱 SAP 指引，如需有關此交易。</span><span class="sxs-lookup"><span data-stu-id="250f9-124">Contact your SAP administrator, or refer to the SAP guidance for more information about this transaction.</span></span>  

  
## <a name="see-also"></a><span data-ttu-id="250f9-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="250f9-125">See Also</span></span>  
 [<span data-ttu-id="250f9-126">使用特定 SAP 配接器實例的 SAP GUI 執行工作</span><span class="sxs-lookup"><span data-stu-id="250f9-126">Performing Tasks Using the SAP GUI for Specific SAP Adapter Scenarios</span></span>](performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)