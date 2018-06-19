---
redirect_url: /biztalk/core/architecture-of-biztalk-adapter-for-peoplesoft-enterprise/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: a277c5f5588a9455119b96f7c600dbadccffb8ac
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24014533"
---
# <a name="peoplesoft-enterprise-requirements"></a>PeopleSoft Enterprise 需求

## <a name="send-handler-requirements"></a>傳送處理常式的需求  
 Microsoft BizTalk Adapter for PeopleSoft Enterprise 包含一個可供人透過 Java API 存取的自訂元件介面 (CI)。 將 `GET_CI_INFO` 這個自訂 CI 物件部署到 PeopleSoft 中 (以提供 BizTalk Adapter for PeopleSoft Enterprise 所需中繼資料資訊) 的方式，是透過 PeopleSoft 工具。 如需詳細資訊，請參閱[安裝企業應用程式介面卡](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md)。  
  
 上傳自訂元件介面是只發生一次。 `GET_CI_INFO.pc` 這個檔案會隨產品安裝，這個檔案必須要安裝好，您才能使用配接器瀏覽 CI。 您必須存取 PeopleSoft 應用程式設計工具。 在 BizTalk Server 電腦上沒有 Application Designer 應用程式。 您可以使用該 Application Designer 將自訂 CI 上傳到您瀏覽的 PeopleSoft 電腦。  
  
 您必須有 PeopleSoft 電腦的存取權，因為您必須設定環境變數 CLASSPATH (或設定資訊**傳輸屬性**螢幕) 以指向 PeopleSoft 的`PSJOA/psjoa.jar`檔案。  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../core/getting-started-with-biztalk-adapter-for-peoplesoft-enterprise.md)   
 