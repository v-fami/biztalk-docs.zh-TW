---
redirect_url: /biztalk/core/installing-biztalk-adapter-for-tibco-rendezvous/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: 4e4209c75ca52585c0a11141dbe0d9841fa6a5ba
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24016017"
---
# <a name="schema-generation-in-the-adapter"></a><span data-ttu-id="da93f-101">在配接器中產生結構描述</span><span class="sxs-lookup"><span data-stu-id="da93f-101">Schema Generation in the Adapter</span></span>
<span data-ttu-id="da93f-102">TIBCO Rendezvous 系統不包含訊息類型儲存機制。</span><span class="sxs-lookup"><span data-stu-id="da93f-102">A TIBCO Rendezvous system does not include a message types repository.</span></span> <span data-ttu-id="da93f-103">所有訊息建構和剖析都是在嵌入在 Rendezvous 應用程式層級。</span><span class="sxs-lookup"><span data-stu-id="da93f-103">All the message construction and parsing is buried at the Rendezvous application level.</span></span> <span data-ttu-id="da93f-104">由於此限制，Microsoft BizTalk Adapter for TIBCO Rendezvous 無法提供結構描述產生功能。</span><span class="sxs-lookup"><span data-stu-id="da93f-104">Because of this limitation, Microsoft BizTalk Adapter for TIBCO Rendezvous cannot provide schema-generation capabilities.</span></span>  
  
## <a name="writing-schemas"></a><span data-ttu-id="da93f-105">撰寫結構描述</span><span class="sxs-lookup"><span data-stu-id="da93f-105">Writing Schemas</span></span>  
 <span data-ttu-id="da93f-106">您必須撰寫結構描述，並使用**加入現有項目**在 Visual Studio 中將它匯入協調流程中使用。</span><span class="sxs-lookup"><span data-stu-id="da93f-106">You must write a schema and use **Add Existing Item** in Visual Studio to import it for use in orchestrations.</span></span> <span data-ttu-id="da93f-107">結構描述對於 BizTalk Server 開發工具以及 Visual Studio 中的整合十分重要。</span><span class="sxs-lookup"><span data-stu-id="da93f-107">Schemas are very important for BizTalk Server development tools and for integration in Visual Studio.</span></span> <span data-ttu-id="da93f-108">BizTalk Server 開發人員可以選擇提供完整的結構描述、精簡的結構描述，或介於兩者之間的版本。</span><span class="sxs-lookup"><span data-stu-id="da93f-108">BizTalk Server developers can choose to provide a complete schema, a minimalist schema, or a version somewhere in between.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da93f-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da93f-109">See Also</span></span>  
 [<span data-ttu-id="da93f-110">快速入門</span><span class="sxs-lookup"><span data-stu-id="da93f-110">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)