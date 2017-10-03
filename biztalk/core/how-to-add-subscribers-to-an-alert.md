---
title: "如何新增訂閱者至警示 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subscriptions, subscribers
- subscriptions
- managing [BAM], adding alert subscribers
ms.assetid: c76a117d-4516-4f48-995c-7e018dbba755
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e86bde9f47e04c17f62c3cacff5d779cf0bed56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-subscribers-to-an-alert"></a><span data-ttu-id="f9628-102">如何新增訂閱者至警示</span><span class="sxs-lookup"><span data-stu-id="f9628-102">How to Add Subscribers to an Alert</span></span>
<span data-ttu-id="f9628-103">系統管理員使用**新增訂閱**命令，將訂閱者新增至指定的警示。</span><span class="sxs-lookup"><span data-stu-id="f9628-103">Administrators use the **add-subscription** command to add a subscriber to a specified alert.</span></span>  
  
### <a name="to-add-subscribers-to-an-alert"></a><span data-ttu-id="f9628-104">新增訂閱者至警示</span><span class="sxs-lookup"><span data-stu-id="f9628-104">To add subscribers to an alert</span></span>  
  
1.  <span data-ttu-id="f9628-105">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f9628-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="f9628-106">在命令提示字元中，輸入 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking，以瀏覽至追蹤資料夾。</span><span class="sxs-lookup"><span data-stu-id="f9628-106">Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt.</span></span> <span data-ttu-id="f9628-107">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f9628-107">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="f9628-108">輸入 `bm add-subscription -View:<view name> -Alert:<alert name> -AccountName:<account name> -Type: [ File | Email ][ -Email:<e-mail address> ]`。</span><span class="sxs-lookup"><span data-stu-id="f9628-108">Type `bm add-subscription -View:<view name> -Alert:<alert name> -AccountName:<account name> -Type: [ File | Email ][ -Email:<e-mail address> ]`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f9628-109">*型別*指定 BAM 用來傳遞警示的傳遞方法。</span><span class="sxs-lookup"><span data-stu-id="f9628-109">*Type* specifies the delivery method which BAM uses to deliver the alert.</span></span> <span data-ttu-id="f9628-110">如果您指定電子郵件的傳遞類型，則必須提供所傳遞警示的目標電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="f9628-110">If you specify a delivery type of e-mail you must supply an e-mail address to which the alert is delivered.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f9628-111">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="f9628-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="f9628-112">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f9628-112">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9628-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9628-113">See Also</span></span>  
 <span data-ttu-id="f9628-114">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="f9628-114">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="f9628-115">[BAM 管理公用程式](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="f9628-115">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="f9628-116">如何從警示移除訂閱者</span><span class="sxs-lookup"><span data-stu-id="f9628-116">How to Remove Subscribers from an Alert</span></span>](../core/how-to-remove-subscribers-from-an-alert.md)