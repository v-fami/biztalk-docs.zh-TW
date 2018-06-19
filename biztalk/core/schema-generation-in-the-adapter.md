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
# <a name="schema-generation-in-the-adapter"></a>在配接器中產生結構描述
TIBCO Rendezvous 系統不包含訊息類型儲存機制。 所有訊息建構和剖析都是在嵌入在 Rendezvous 應用程式層級。 由於此限制，Microsoft BizTalk Adapter for TIBCO Rendezvous 無法提供結構描述產生功能。  
  
## <a name="writing-schemas"></a>撰寫結構描述  
 您必須撰寫結構描述，並使用**加入現有項目**在 Visual Studio 中將它匯入協調流程中使用。 結構描述對於 BizTalk Server 開發工具以及 Visual Studio 中的整合十分重要。 BizTalk Server 開發人員可以選擇提供完整的結構描述、精簡的結構描述，或介於兩者之間的版本。  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)