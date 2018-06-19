---
title: Wcf-customisolated 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-CustomIsolated adapters
ms.assetid: 0b529992-65e4-4543-951f-61644f8315a0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 734986a7ea87ff3b5a4b4a46a307d44665246b22
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288494"
---
# <a name="wcf-customisolated-adapter"></a><span data-ttu-id="2ac24-102">WCF-CustomIsolated 配接器</span><span class="sxs-lookup"><span data-stu-id="2ac24-102">WCF-CustomIsolated Adapter</span></span>
<span data-ttu-id="2ac24-103">Wcf-customisolated 配接器是外掛式配接器來設定透過 HTTP 傳輸接收位置的任何繫結和行為設定 Windows Communication Foundation (WCF) 適用於[!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2ac24-103">The WCF-CustomIsolated adapter is an isolated adapter to allow configuring receive locations over the HTTP transport with any binding and behavior settings for Windows Communication Foundation (WCF) that are applicable to [!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="2ac24-104">WCF-CustomIsolated 配接器可以用於標準 WCF 配接器所不支援的實例。</span><span class="sxs-lookup"><span data-stu-id="2ac24-104">You can use the WCF-CustomIsolated adapter for scenarios that the standard WCF adapters do not support.</span></span> <span data-ttu-id="2ac24-105">WCF-CustomIsolated 配接器也可以讓您使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 WCF 擴充性點。</span><span class="sxs-lookup"><span data-stu-id="2ac24-105">The WCF-CustomIsolated adapter also enables you to use the WCF extensibility points in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2ac24-106">WCF-CustomIsolated 配接器是用於外掛式主控件中執行的接收位置。</span><span class="sxs-lookup"><span data-stu-id="2ac24-106">The WCF-CustomIsolated adapter is used for the receive location running in an isolated host.</span></span> <span data-ttu-id="2ac24-107">若要使用 WCF-CustomIsolated 配接器，您必須使用 BizTalk WCF 服務發佈精靈，在 Microsoft Internet Information Services (IIS) 中建立對應這個接收位置的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="2ac24-107">To use the WCF-CustomIsolated adapter, you must use the BizTalk WCF Service Publishing Wizard to create in Microsoft Internet Information Services (IIS) the virtual directory corresponding to this receive location.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2ac24-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="2ac24-108">In This Section</span></span>  
  
-   [<span data-ttu-id="2ac24-109">Wcf-customisolated 配接器為何？</span><span class="sxs-lookup"><span data-stu-id="2ac24-109">What Is the WCF-CustomIsolated Adapter?</span></span>](../core/what-is-the-wcf-customisolated-adapter.md)  
  
-   [<span data-ttu-id="2ac24-110">設定 Wcf-customisolated 配接器</span><span class="sxs-lookup"><span data-stu-id="2ac24-110">Configuring the WCF-CustomIsolated Adapter</span></span>](../core/configuring-the-wcf-customisolated-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="2ac24-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ac24-111">See Also</span></span>  
 [<span data-ttu-id="2ac24-112">擴充性簡介</span><span class="sxs-lookup"><span data-stu-id="2ac24-112">Introduction to Extensibility</span></span>](http://go.microsoft.com/fwlink/?LinkId=82590)