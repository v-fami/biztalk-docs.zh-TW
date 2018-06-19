---
title: 設定 WCF 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- NetTcpBinding [WCF adapters]
- configuring [WCF adapters]
- WCF adapters, pre-defined bindings
- configuring [WCF adapters], about configuring WCF adapters
- WsHttpBinding [WCF adapters]
- BasicHttpBinding [WCF adapters]
- NetNamedPipeBinding [WCF adapters]
- NetMsmqBinding [WCF adapters]
- bindings, pre-defined [WCF adapters]
- WCF adapters, configuring
ms.assetid: af01e2d4-303d-407a-b853-dd90b0246a8a
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dde69bb5b2014a20509778e27230840e47c0b36d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233158"
---
# <a name="configuring-the-wcf-adapters"></a><span data-ttu-id="64641-102">設定 WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="64641-102">Configuring the WCF Adapters</span></span>
<span data-ttu-id="64641-103">適用於 Windows Communication Foundation (WCF) 的 BizTalk 配接器讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 能與 WCF 應用程式通訊。</span><span class="sxs-lookup"><span data-stu-id="64641-103">The BizTalk Adapters for Windows Communication Foundation (WCF) allow  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to communicate with WCF-based applications.</span></span> <span data-ttu-id="64641-104">BizTalk WCF 配接器包括表示 WCF 預先定義繫結的五個實體配接器 —**BasicHttpBinding**， **WsHttpBinding**， **NetTcpBinding**， **NetNamedPipeBinding**，和**NetMsmqBinding**。</span><span class="sxs-lookup"><span data-stu-id="64641-104">The BizTalk WCF adapters include five physical adapters that represent the WCF predefined bindings—**BasicHttpBinding**, **WsHttpBinding**, **NetTcpBinding**, **NetNamedPipeBinding**, and **NetMsmqBinding**.</span></span> <span data-ttu-id="64641-105">提供這些表示預先定義繫結之 WCF 配接器的目的，是要讓您能夠輕鬆設定多數應用程式需求的必要資訊。</span><span class="sxs-lookup"><span data-stu-id="64641-105">The WCF adapters for the predefined bindings are provided to enable you to easily configure necessary information for most application requirements.</span></span>  
  
 <span data-ttu-id="64641-106">BizTalk WCF 配接器也包括兩個配接器，可讓您針對接收位置和傳送埠，自由設定 WCF 繫結和行為資訊。</span><span class="sxs-lookup"><span data-stu-id="64641-106">The BizTalk WCF adapters also include two adapters that enable you to freely configure WCF binding and behavior information for the receive location and send port.</span></span>  
  
 <span data-ttu-id="64641-107">所有 WCF 配接器都會提供類似的傳輸屬性對話方塊來設定傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="64641-107">All the WCF adapters provide similar transport properties dialog boxes for send ports and receive locations.</span></span> <span data-ttu-id="64641-108">不過，視實體配接器而定，設定 WCF 配接器的詳細工作會不同。</span><span class="sxs-lookup"><span data-stu-id="64641-108">However, the detailed tasks to configure the WCF adapters vary depending on the physical adapter.</span></span> <span data-ttu-id="64641-109">與配接器繫結沒有直接相關的工作 (例如安裝憑證)，對所有 WCF 配接器來說都是相同的。</span><span class="sxs-lookup"><span data-stu-id="64641-109">Tasks not directly related to the adapter bindings, such as installing certificates, are the same for all the WCF adapters.</span></span> <span data-ttu-id="64641-110">本節將探討所有 WCF 配接器的一般工作。</span><span class="sxs-lookup"><span data-stu-id="64641-110">This section discusses the tasks that are common to all the WCF adapters.</span></span> <span data-ttu-id="64641-111">每個介面卡不同工作的詳細資訊，請參閱中的配接器的適當主題[WCF 配接器](../core/wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="64641-111">For information about tasks that differ for each adapter, see the appropriate topics for the adapter in [WCF Adapters](../core/wcf-adapters.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64641-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="64641-112">In This Section</span></span>  
  
-   [<span data-ttu-id="64641-113">WCF 配接器屬性結構描述和屬性</span><span class="sxs-lookup"><span data-stu-id="64641-113">WCF Adapters Property Schema and Properties</span></span>](../core/wcf-adapters-property-schema-and-properties.md)  
  
-   [<span data-ttu-id="64641-114">WCF 配接器安全性建議</span><span class="sxs-lookup"><span data-stu-id="64641-114">WCF Adapters Security Recommendations</span></span>](../core/wcf-adapters-security-recommendations.md)  
  
-   [<span data-ttu-id="64641-115">WCF 配接器安裝憑證</span><span class="sxs-lookup"><span data-stu-id="64641-115">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)  
  
-   [<span data-ttu-id="64641-116">指定訊息本文為 WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="64641-116">Specifying the Message Body for the WCF Adapters</span></span>](../core/specifying-the-message-body-for-the-wcf-adapters.md)  
  
-   [<span data-ttu-id="64641-117">如何啟用 WCF 擴充性點，WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="64641-117">How to Enable the WCF Extensibility Points with the WCF Adapters</span></span>](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md)  
  
-   [<span data-ttu-id="64641-118">WCF 配接器效能計數器</span><span class="sxs-lookup"><span data-stu-id="64641-118">WCF Adapters Performance Counters</span></span>](../core/wcf-adapters-performance-counters.md)  
  
-   [<span data-ttu-id="64641-119">WCF 配接器的單一登入支援</span><span class="sxs-lookup"><span data-stu-id="64641-119">Single Sign-On Support for the WCF Adapters</span></span>](../core/single-sign-on-support-for-the-wcf-adapters.md)  
  
## <a name="see-also"></a><span data-ttu-id="64641-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64641-120">See Also</span></span>  
 [<span data-ttu-id="64641-121">WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="64641-121">WCF Adapters</span></span>](../core/wcf-adapters.md)