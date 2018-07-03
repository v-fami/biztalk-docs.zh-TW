---
title: 在細分接收位置之後，接收 Oracle E-business Suite 資料庫變更通知 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 12c42cd0-b46e-4c45-a67e-e1fb9c0e8a6d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43ae3972bf310528dbf17014c7f3db14ca3ea63c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996479"
---
# <a name="receive-oracle-e-business-suite-database-change-notifications-after-a-receive-location-breakdown"></a><span data-ttu-id="174ee-102">在細分接收位置之後，接收 Oracle E-business Suite 資料庫變更通知</span><span class="sxs-lookup"><span data-stu-id="174ee-102">Receive Oracle E-Business Suite database change notifications after a receive location breakdown</span></span>
<span data-ttu-id="174ee-103">假設您有 ACCOUNTACTIVITY 資料表受到變更時，接收資料庫變更通知訊息的 BizTalk 應用程式的位置。</span><span class="sxs-lookup"><span data-stu-id="174ee-103">Consider a scenario where you have a BizTalk application that receives database change notification messages when changes are made to the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="174ee-104">如果接收位置設定為一部分的 BizTalk 應用程式細分，同時新增到 ACCOUNTACTIVITY 資料表的記錄，您不會收到通知的最近新增的記錄。</span><span class="sxs-lookup"><span data-stu-id="174ee-104">If the receive location configured as part of the BizTalk application breaks down, and simultaneously records are added into the ACCOUNTACTIVITY table, you will not receive notifications for the recently added records.</span></span> <span data-ttu-id="174ee-105">您也不會知道接收位置再次可用時。</span><span class="sxs-lookup"><span data-stu-id="174ee-105">You will also not know when the receive location is available again.</span></span> <span data-ttu-id="174ee-106">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會公開繫結屬性， **NotifyOnListenerStart**，您可以設定為會收到通知，接收位置已復原。</span><span class="sxs-lookup"><span data-stu-id="174ee-106">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes a binding property, **NotifyOnListenerStart**, that you can configure to get a notification that the receive location has recovered.</span></span> <span data-ttu-id="174ee-107">您可以指定下列值**NotifyOnListenerStart**繫結屬性：</span><span class="sxs-lookup"><span data-stu-id="174ee-107">You can specify the following values for the **NotifyOnListenerStart** binding property:</span></span>  
  
- <span data-ttu-id="174ee-108">將此屬性設定為 **，則為 True**，以接收通知，通知的接收位置的話，只要接收位置復原。</span><span class="sxs-lookup"><span data-stu-id="174ee-108">Set this property to **True**, to receive a notification informing that the receive location is available, as soon as the receive location recovers.</span></span>  
  
- <span data-ttu-id="174ee-109">將此屬性設定為**False**，而不會收到通知，通知的接收位置接收位置復原後有的話。</span><span class="sxs-lookup"><span data-stu-id="174ee-109">Set this property to **False**, to not receive a notification informing that the receive location is available, after the receive location recovers.</span></span>  
  
  <span data-ttu-id="174ee-110">預設值是 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="174ee-110">Default is **True**.</span></span>  
  
## <a name="configuring-the-oracle-e-business-adapter-behavior"></a><span data-ttu-id="174ee-111">設定 Oracle E-business 配接器行為</span><span class="sxs-lookup"><span data-stu-id="174ee-111">Configuring the Oracle E-Business Adapter Behavior</span></span>  
 <span data-ttu-id="174ee-112">針對任一種方法，您不需要產生中繼資料時，或在設定 BizTalk 應用程式時，執行任何特定的工作。</span><span class="sxs-lookup"><span data-stu-id="174ee-112">For either of the approaches, you do not need to perform any specific tasks while generating metadata or while configuring the BizTalk application.</span></span> <span data-ttu-id="174ee-113">您只需要設定**NotifyOnListenerStart**屬性繫結據此在 WCF 自訂 」 或 「 Wcf-oracleebs 上接收位置。</span><span class="sxs-lookup"><span data-stu-id="174ee-113">You only need to set the **NotifyOnListenerStart** binding property accordingly on the WCF-Custom or WCF-OracleEBS receive location.</span></span> <span data-ttu-id="174ee-114">若要建立的 BizTalk 應用程式，您必須執行同一組工作中所述[接收 Oracle E-business Suite 變更通知以累加方式使用 BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-change-notifications-incrementally-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="174ee-114">To create the BizTalk application, you must perform the same set of tasks as described in [Receive Oracle E-Business Suite Change Notifications Incrementally Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-change-notifications-incrementally-using-biztalk-server.md).</span></span> <span data-ttu-id="174ee-115">不過，設定 BizTalk 應用程式使用時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以嘗試變更的值**NotifyOnListenerStart**屬性繫結，並查看兩個組態的差異。</span><span class="sxs-lookup"><span data-stu-id="174ee-115">However, when configuring the BizTalk application using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you can try changing the value of **NotifyOnListenerStart** binding property and see the difference in the two configurations.</span></span>  
  
 <span data-ttu-id="174ee-116">下圖示範如何在收到通知後根據的值**NotifyOnListenerStart**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="174ee-116">The following figure demonstrates how the notifications are received based on the value of the **NotifyOnListenerStart** binding property.</span></span>  
  
 <span data-ttu-id="174ee-117">![設定 SQL 配接器的通知](../../adapters-and-accelerators/adapter-oracle-database/media/4018300a-1a58-47da-ac9d-c77c13d7081d.gif "4018300a-1a58-47da-ac9d-c77c13d7081d")</span><span class="sxs-lookup"><span data-stu-id="174ee-117">![Configure SQL Adapter for notifications](../../adapters-and-accelerators/adapter-oracle-database/media/4018300a-1a58-47da-ac9d-c77c13d7081d.gif "4018300a-1a58-47da-ac9d-c77c13d7081d")</span></span>  
  
 <span data-ttu-id="174ee-118">請注意，在第一個案例中，當**NotifyOnListenerStart**設為 **，則為 True**並記錄插入資料庫資料表向下接收位置時，配接器只會傳送給您當接收位置出現時，就會通知訊息。</span><span class="sxs-lookup"><span data-stu-id="174ee-118">Note that in the first scenario, when the **NotifyOnListenerStart** is set to **True** and records are inserted into the database table while the receive location was down, the adapter only sends you a notification message when the receive location comes up.</span></span> <span data-ttu-id="174ee-119">配接器不會執行任何作業來處理已插入向下接收位置時的記錄。</span><span class="sxs-lookup"><span data-stu-id="174ee-119">The adapter does not perform any operation to process the records that were inserted while the receive location was down.</span></span> <span data-ttu-id="174ee-120">配接器用戶端必須實作相關的邏輯來處理已插入向下接收位置時記錄其應用程式中。</span><span class="sxs-lookup"><span data-stu-id="174ee-120">The adapter client must implement the relevant logic in their application to process the records that were inserted while the receive location was down.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="174ee-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="174ee-121">See Also</span></span>  
 [<span data-ttu-id="174ee-122">Oracle E-business Suite 使用接收資料庫變更通知 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="174ee-122">Receive Oracle E-Business Suite Database Change Notifications Using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-using-biztalk-server.md)