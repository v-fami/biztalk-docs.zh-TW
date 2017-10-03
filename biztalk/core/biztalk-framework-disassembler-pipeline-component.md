---
title: "BizTalk Framework 解譯器管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, BizTalk Framework Disassembler
- BizTalk Framework Disassembler [pipeline component]
ms.assetid: 48d6c530-5c02-4c70-ad11-0ea6c3c808f8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1ab54ddb9ef0b5fa389e6716fc4426978dcbd7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-framework-disassembler-pipeline-component"></a><span data-ttu-id="3b928-102">BizTalk Framework 解譯器管線元件</span><span class="sxs-lookup"><span data-stu-id="3b928-102">BizTalk Framework Disassembler Pipeline Component</span></span>
<span data-ttu-id="3b928-103">BizTalk Framework 解譯器管線元件會剖析 XML 資料，並判斷它是否包含 BizTalk Framework 類型的傳訊內容。</span><span class="sxs-lookup"><span data-stu-id="3b928-103">The BizTalk Framework Disassembler pipeline component parses XML data and determines whether it contains a BizTalk Framework-based messaging payload.</span></span> <span data-ttu-id="3b928-104">管線元件會儲存訊息內容，以及透過需要產生的 BizTalk Framework 屬性建立新的訊息內容。</span><span class="sxs-lookup"><span data-stu-id="3b928-104">The pipeline component saves the message context, and a new message context is created with the BizTalk Framework property that needs to be generated.</span></span> <span data-ttu-id="3b928-105">此屬性用以將訊息路由到 BizTalk Framework 輸入處理常式，以便接收訊息進行處理。</span><span class="sxs-lookup"><span data-stu-id="3b928-105">This property is used to route the message to the BizTalk Framework inbound handler, so it can receive the message to process.</span></span>  
  
 <span data-ttu-id="3b928-106">若傳送者要求在 BizTalk Framework 信封內使用 deliverReceiptRequest 標頭，則 BizTalk Framework 解譯器管線元件會為產生的訊息產生一個通知。</span><span class="sxs-lookup"><span data-stu-id="3b928-106">The BizTalk Framework Disassembler pipeline component generates an acknowledgment for the generated message if the sender requested one using the deliverReceiptRequest header within the BizTalk Framework envelope.</span></span> <span data-ttu-id="3b928-107">這是由 BizTalk Framework 組合器管線元件中的產生送達回條屬性所控制。</span><span class="sxs-lookup"><span data-stu-id="3b928-107">This is controlled by the generate delivery receipt property in the BizTalk Framework Assembler pipeline component.</span></span> <span data-ttu-id="3b928-108">如需 BizTalk Framework 的詳細資訊，請參閱[BizTalk Framework 組合器管線元件](../core/biztalk-framework-assembler-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="3b928-108">For more information about the BizTalk Framework, see [BizTalk Framework Assembler Pipeline Component](../core/biztalk-framework-assembler-pipeline-component.md).</span></span>  
  
 <span data-ttu-id="3b928-109">如需設定 BizTalk Framework 解譯器管線元件和建立協調流程的資訊，請參閱[如何設定 BizTalk Framework 解譯器管線元件](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="3b928-109">For information about configuring the BizTalk Framework Disassembler pipeline component and creating the orchestration, see [How to Configure the BizTalk Framework Disassembler Pipeline Component](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b928-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b928-110">See Also</span></span>  
 <span data-ttu-id="3b928-111">[如何設定 BizTalk Framework 解譯器管線元件](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="3b928-111">[How to Configure the BizTalk Framework Disassembler Pipeline Component](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="3b928-112">管線元件</span><span class="sxs-lookup"><span data-stu-id="3b928-112">Pipeline Components</span></span>](../core/pipeline-components.md)