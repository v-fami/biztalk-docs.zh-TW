---
title: 開發自訂元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 12b7d99d-ac3c-427d-b6b6-286233fde541
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b61144b2acaf787d56468c23c04835b5ad79324
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239262"
---
# <a name="developing-custom-components"></a><span data-ttu-id="00db7-102">開發自訂元件</span><span class="sxs-lookup"><span data-stu-id="00db7-102">Developing Custom Components</span></span>
<span data-ttu-id="00db7-103">您可以在 BizTalk Server 中開發和使用自訂元件，來修改或擴充 BizTalk Server 的特定基礎結構項目。</span><span class="sxs-lookup"><span data-stu-id="00db7-103">Custom components in BizTalk Server are developed and used to modify or extend certain infrastructure elements of BizTalk Server.</span></span>  <span data-ttu-id="00db7-104">主要，這包括： 傳送或接收配接器元件會根據配接器架構，且用來處理特定傳輸通訊協定。管線元件用在任何傳送或接收管線階段。與運算質在對應中使用。</span><span class="sxs-lookup"><span data-stu-id="00db7-104">Primarily, this includes such things as:  send or receive adapter components which are based on the Adapter Framework and used to handle specific transport protocols; pipeline components used in any of the send or receive pipeline stages; and functoids used in maps.</span></span>  <span data-ttu-id="00db7-105">您可以透過自訂程式碼，以數種方式擴充 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="00db7-105">You can extend [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with custom code in several ways.</span></span> <span data-ttu-id="00db7-106">下列主題說明執行此作業的方法。</span><span class="sxs-lookup"><span data-stu-id="00db7-106">The following topics describe how to do this.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00db7-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="00db7-107">In This Section</span></span>  
  
-   [<span data-ttu-id="00db7-108">開發自訂配接器</span><span class="sxs-lookup"><span data-stu-id="00db7-108">Developing Custom Adapters</span></span>](../core/developing-custom-adapters.md)  
  
-   [<span data-ttu-id="00db7-109">開發自訂管線元件</span><span class="sxs-lookup"><span data-stu-id="00db7-109">Developing Custom Pipeline Components</span></span>](../core/developing-custom-pipeline-components.md)  
  
-   [<span data-ttu-id="00db7-110">開發自訂運算質</span><span class="sxs-lookup"><span data-stu-id="00db7-110">Developing Custom Functoids</span></span>](../core/developing-custom-functoids.md)