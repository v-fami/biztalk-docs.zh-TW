---
title: ESB 發送器解譯元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b1f5e46b-8f41-47f8-b22b-b9e9eaac6475
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c846ca716aef72d43e4f4a6ed75a2b20a81c351a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294686"
---
# <a name="the-esb-dispatcher-disassemble-component"></a><span data-ttu-id="fec86-102">ESB 發送器解譯元件</span><span class="sxs-lookup"><span data-stu-id="fec86-102">The ESB Dispatcher Disassemble Component</span></span>
<span data-ttu-id="fec86-103">ESB 發送器解譯元件可以動態設定輸出訊息的端點位置屬性至發送器元件類似的方式。</span><span class="sxs-lookup"><span data-stu-id="fec86-103">The ESB Dispatcher Disassemble component can dynamically set endpoint location properties for outbound messages in a similar way to the Dispatcher component.</span></span> <span data-ttu-id="fec86-104">此管線元件會結合取消批次功能的 Microsoft BizTalk 訊息 (透過繼承自 XML 解譯器類別，名為**XmlDasmComp**) 與訊息分派機制，可以執行 ESB 行程BizTalk 管線中的訊息服務。</span><span class="sxs-lookup"><span data-stu-id="fec86-104">This pipeline component combines Microsoft BizTalk message de-batching functionality (by inheriting from the XML disassembler class named **XmlDasmComp**) with the message dispatching mechanism that can execute ESB itinerary messaging services in a BizTalk pipeline.</span></span>