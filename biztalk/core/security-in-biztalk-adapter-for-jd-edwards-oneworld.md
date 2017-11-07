---
title: "使用 SSO 安全 JD Edwards OneWorld |Microsoft 文件"
description: "在 BizTalk Server 中使用 Microsoft BizTalk 配接器的 JD Edwards OneWorld 時的安全性概觀"
ms.custom: 
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: beb736a8-d95f-4d44-a882-2d437c4892f4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97e72ffbc38cad2f5bbd622ed497663cf8ac5f3c
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="security-in-jd-edwards-oneworld"></a><span data-ttu-id="3b1de-103">JD Edwards OneWorld 中的安全性</span><span class="sxs-lookup"><span data-stu-id="3b1de-103">Security in JD Edwards OneWorld</span></span>

## <a name="overview"></a><span data-ttu-id="3b1de-104">概觀</span><span class="sxs-lookup"><span data-stu-id="3b1de-104">Overview</span></span>
<span data-ttu-id="3b1de-105">Microsoft BizTalk Adapter for JD Edwards OneWorld 提供單一登入 (SSO) 支援 。</span><span class="sxs-lookup"><span data-stu-id="3b1de-105">Microsoft BizTalk Adapter for JD Edwards OneWorld provides Single Sign-On (SSO) support.</span></span> <span data-ttu-id="3b1de-106">由企業單一登入工具所建立的分支機構應用程式，代表像是 JD Edwards OneWorld 的伺服器系統。</span><span class="sxs-lookup"><span data-stu-id="3b1de-106">An affiliate application created by Enterprise Single Sign-On tools represents a server system such as JD Edwards OneWorld.</span></span>  

<span data-ttu-id="3b1de-107">本節提供如何在安全環境中部署 Microsoft BizTalk Adapter for JD Edwards OneWorld 的指導方針。</span><span class="sxs-lookup"><span data-stu-id="3b1de-107">This section provides guidelines about how to deploy Microsoft BizTalk Adapter for JD Edwards OneWorld in a secure environment.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="3b1de-108">我們建議您限制只有，授權使用者才能使用 BizTalk Adapter for JD Edwards OneWorld 特定業務應用程式在直接連接的用戶端檔案。</span><span class="sxs-lookup"><span data-stu-id="3b1de-108">We recommended that you restrict the use of BizTalk Adapter for JD Edwards OneWorld to authorized users only, as the client files directly connect to the line-of-business applications.</span></span>  

## <a name="next-steps"></a><span data-ttu-id="3b1de-109">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="3b1de-109">Next steps</span></span>
  
-   [<span data-ttu-id="3b1de-110">單一登入的需求</span><span class="sxs-lookup"><span data-stu-id="3b1de-110">Requirements for Single Sign-On</span></span>](../core/requirements-for-single-sign-on5.md)  
  
-   [<span data-ttu-id="3b1de-111">單一登入與 BizTalk Adapter for JD Enterprise OneWorld</span><span class="sxs-lookup"><span data-stu-id="3b1de-111">Single Sign-On and BizTalk Adapter for JD Enterprise OneWorld</span></span>](../core/single-sign-on-and-biztalk-adapter-for-jd-enterprise-oneworld.md)  
  
-   [<span data-ttu-id="3b1de-112">建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="3b1de-112">Creating Affiliate Applications</span></span>](../core/creating-affiliate-applications3.md)  
  
-   [<span data-ttu-id="3b1de-113">設定虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="3b1de-113">Configuring the Virtual Directory</span></span>](../core/configuring-the-virtual-directory.md)  
  
-   [<span data-ttu-id="3b1de-114">如何設定 HTTP 接收配接器</span><span class="sxs-lookup"><span data-stu-id="3b1de-114">How to Configure the HTTP Receive Adapter</span></span>](../core/how-to-configure-the-http-receive-adapter2.md)  
  
-   [<span data-ttu-id="3b1de-115">建立傳送和接收埠</span><span class="sxs-lookup"><span data-stu-id="3b1de-115">Creating Send and Receive Ports</span></span>](../core/creating-send-and-receive-ports.md)  
  
-   [<span data-ttu-id="3b1de-116">將結構描述匯入至 BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="3b1de-116">Importing Schemas into BizTalk Server Projects</span></span>](../core/importing-schemas-into-biztalk-server-projects1.md)  
  
-   [<span data-ttu-id="3b1de-117">執行中的協調流程</span><span class="sxs-lookup"><span data-stu-id="3b1de-117">Running Orchestrations</span></span>](../core/running-orchestrations1.md)  
  
-   [<span data-ttu-id="3b1de-118">執行 SSO 專案</span><span class="sxs-lookup"><span data-stu-id="3b1de-118">Running SSO Projects</span></span>](../core/running-sso-projects3.md)