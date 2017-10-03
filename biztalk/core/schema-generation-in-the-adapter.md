---
title: "配接器中的結構描述產生 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, generating
- writing, schemas
ms.assetid: 43b69383-bae0-401b-9620-d4302db799b2
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d10d927e4ede59e716b3f9838c96bac8cd144a81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="schema-generation-in-the-adapter"></a><span data-ttu-id="fa40a-102">在配接器中產生結構描述</span><span class="sxs-lookup"><span data-stu-id="fa40a-102">Schema Generation in the Adapter</span></span>
<span data-ttu-id="fa40a-103">TIBCO Rendezvous 系統不包含訊息類型儲存機制。</span><span class="sxs-lookup"><span data-stu-id="fa40a-103">A TIBCO Rendezvous system does not include a message types repository.</span></span> <span data-ttu-id="fa40a-104">所有訊息建構和剖析都是在嵌入在 Rendezvous 應用程式層級。</span><span class="sxs-lookup"><span data-stu-id="fa40a-104">All the message construction and parsing is buried at the Rendezvous application level.</span></span> <span data-ttu-id="fa40a-105">由於此限制，Microsoft BizTalk Adapter for TIBCO Rendezvous 無法提供結構描述產生功能。</span><span class="sxs-lookup"><span data-stu-id="fa40a-105">Because of this limitation, Microsoft BizTalk Adapter for TIBCO Rendezvous cannot provide schema-generation capabilities.</span></span>  
  
## <a name="writing-schemas"></a><span data-ttu-id="fa40a-106">撰寫結構描述</span><span class="sxs-lookup"><span data-stu-id="fa40a-106">Writing Schemas</span></span>  
 <span data-ttu-id="fa40a-107">您必須撰寫結構描述，並使用**加入現有項目**在 Visual Studio 中將它匯入協調流程中使用。</span><span class="sxs-lookup"><span data-stu-id="fa40a-107">You must write a schema and use **Add Existing Item** in Visual Studio to import it for use in orchestrations.</span></span> <span data-ttu-id="fa40a-108">結構描述對於 BizTalk Server 開發工具以及 Visual Studio 中的整合十分重要。</span><span class="sxs-lookup"><span data-stu-id="fa40a-108">Schemas are very important for BizTalk Server development tools and for integration in Visual Studio.</span></span> <span data-ttu-id="fa40a-109">BizTalk Server 開發人員可以選擇提供完整的結構描述、精簡的結構描述，或介於兩者之間的版本。</span><span class="sxs-lookup"><span data-stu-id="fa40a-109">BizTalk Server developers can choose to provide a complete schema, a minimalist schema, or a version somewhere in between.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa40a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa40a-110">See Also</span></span>  
 [<span data-ttu-id="fa40a-111">快速入門</span><span class="sxs-lookup"><span data-stu-id="fa40a-111">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)