---
title: 執行 BizTalk Server 的電腦備份 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70f53b41-8083-4b56-8698-e75a13b21a69
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 537ea40b39ecd35127b62f8d96f0175e98a1f3b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230502"
---
# <a name="backing-up-a-computer-running-biztalk-server"></a><span data-ttu-id="86fa4-102">對執行 BizTalk Server 的電腦進行備份</span><span class="sxs-lookup"><span data-stu-id="86fa4-102">Backing Up a Computer Running BizTalk Server</span></span>
<span data-ttu-id="86fa4-103">執行 BizTalk Server 的電腦若發生無法修復的硬體失敗，您就必須用一模一樣的電腦予以替換。</span><span class="sxs-lookup"><span data-stu-id="86fa4-103">If a computer running BizTalk Server suffers an irrecoverable hardware failure, then you must replace that computer with an identical one.</span></span> <span data-ttu-id="86fa4-104">您應該設定在替換的電腦具有基底平台軟體、 軟體必要元件，BizTalk Server 元件和相同的組態設定。</span><span class="sxs-lookup"><span data-stu-id="86fa4-104">You should set up the replacement computer with the base platform software, software prerequisites, BizTalk Server components, and identical configuration settings.</span></span> <span data-ttu-id="86fa4-105">這些組態設定可能包括適用的登錄項目、檔案和資料夾，還有 BizTalk 應用程式正常運作所需的相關 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="86fa4-105">These configuration settings may consist of the appropriate registry entries, files, folders, and related Windows services necessary for the correct operation of your BizTalk applications.</span></span>  
  
 <span data-ttu-id="86fa4-106">除了備份 BizTalk Server 資料庫之外，請一併備份下列 BizTalk Server 元件，以確保硬體失敗後能夠復原 BizTalk Server：</span><span class="sxs-lookup"><span data-stu-id="86fa4-106">In addition to backing up the BizTalk Server databases, you should back up the following BizTalk Server components to ensure that you can recover BizTalk Server after a hardware failure:</span></span>  
  
-   <span data-ttu-id="86fa4-107">BizTalk Server 組態</span><span class="sxs-lookup"><span data-stu-id="86fa4-107">BizTalk Server configuration</span></span>  
  
-   <span data-ttu-id="86fa4-108">企業單一登入 (SSO) 主要密碼</span><span class="sxs-lookup"><span data-stu-id="86fa4-108">Enterprise Single Sign-On (SSO) master secret</span></span>  
  
-   <span data-ttu-id="86fa4-109">商務活動監控 (BAM) 入口網站 (若有使用 BAM 才需要)</span><span class="sxs-lookup"><span data-stu-id="86fa4-109">Business Activity Monitoring (BAM) portal (not required unless you're using BAM)</span></span>  
  
-   <span data-ttu-id="86fa4-110">BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="86fa4-110">BizTalk applications</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86fa4-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="86fa4-111">In This Section</span></span>  
  
-   [<span data-ttu-id="86fa4-112">如何備份 BizTalk Server 組態</span><span class="sxs-lookup"><span data-stu-id="86fa4-112">How to Back Up The BizTalk Server Configuration</span></span>](../core/how-to-back-up-the-biztalk-server-configuration.md)  
  
-   [<span data-ttu-id="86fa4-113">如何備份主要密碼</span><span class="sxs-lookup"><span data-stu-id="86fa4-113">How to Back Up the Master Secret</span></span>](../core/how-to-back-up-the-master-secret.md)  
  
-   [<span data-ttu-id="86fa4-114">如何備份 BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="86fa4-114">How to Back Up the BAM Portal</span></span>](../core/how-to-back-up-the-bam-portal.md)  
  
-   [<span data-ttu-id="86fa4-115">備份 BizTalk Server 應用程式</span><span class="sxs-lookup"><span data-stu-id="86fa4-115">Backing Up BizTalk Server Applications</span></span>](../core/backing-up-biztalk-server-applications.md)