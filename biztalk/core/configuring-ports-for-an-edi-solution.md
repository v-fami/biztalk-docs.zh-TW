---
title: 設定 EDI 解決方案的連接埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94445da5-9ee0-4006-a8c2-3919f128a575
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 779965c05a5875295fd28e74df6ceacd5037cd2d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233134"
---
# <a name="configuring-ports-for-an-edi-solution"></a><span data-ttu-id="eb694-102">設定 EDI 解決方案的連接埠</span><span class="sxs-lookup"><span data-stu-id="eb694-102">Configuring Ports for an EDI Solution</span></span>
<span data-ttu-id="eb694-103">若要接收和傳送 EDI 訊息與通知，請建立下列接收埠與傳送埠：</span><span class="sxs-lookup"><span data-stu-id="eb694-103">To receive and send EDI messages and acknowledgments, create the following receive and send ports:</span></span>  
  
-   <span data-ttu-id="eb694-104">接收 EDI 交換和通知的單向靜態 FILE 接收埠，或接收 EDI 交換和傳送通知的雙向要求-回應 FILE 接收埠。</span><span class="sxs-lookup"><span data-stu-id="eb694-104">A one-way static FILE receive port that receives EDI interchanges and acknowledgments or a two-way request-response FILE receive port that receives EDI interchanges and sends acknowledgments.</span></span>  
  
-   <span data-ttu-id="eb694-105">傳送 EDI 交換或通知的單向 FILE 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="eb694-105">A one-way FILE send port that sends EDI interchanges or acknowledgments.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eb694-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="eb694-106">In This Section</span></span>  
  
-   [<span data-ttu-id="eb694-107">設定連接埠來接收 EDI 訊息和通知</span><span class="sxs-lookup"><span data-stu-id="eb694-107">Configuring a Port to Receive EDI Messages and Acknowledgments</span></span>](../core/configuring-a-port-to-receive-edi-messages-and-acknowledgments.md)  
  
-   [<span data-ttu-id="eb694-108">設定靜態傳送埠以傳送 EDI 交換和通知</span><span class="sxs-lookup"><span data-stu-id="eb694-108">Configuring a Static Send Port to Send EDI Interchanges and Acknowledgments</span></span>](../core/configuring-a-static-send-port-to-send-edi-interchanges-and-acknowledgments.md)  
  
-   [<span data-ttu-id="eb694-109">設定動態傳送埠以傳送 EDI 交換和通知</span><span class="sxs-lookup"><span data-stu-id="eb694-109">Configuring a Dynamic Send Port to Send EDI Interchanges and Acknowledgments</span></span>](../core/configuring-a-dynamic-send-port-to-send-edi-interchanges-and-acknowledgments.md)  
  
-   [<span data-ttu-id="eb694-110">啟用接收單一訊息中的多重交換</span><span class="sxs-lookup"><span data-stu-id="eb694-110">Enabling the Receiving of Multiple Interchanges in a Single Message</span></span>](../core/enabling-the-receiving-of-multiple-interchanges-in-a-single-message.md)  
  
## <a name="see-also"></a><span data-ttu-id="eb694-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb694-111">See Also</span></span>  
 [<span data-ttu-id="eb694-112">開發和設定 BizTalk Server EDI 解決方案</span><span class="sxs-lookup"><span data-stu-id="eb694-112">Developing and Configuring BizTalk Server EDI Solutions</span></span>](../core/developing-and-configuring-biztalk-server-edi-solutions.md)