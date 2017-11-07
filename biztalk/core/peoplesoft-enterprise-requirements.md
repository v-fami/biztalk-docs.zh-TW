---
redirect_url: /biztalk/core/architecture-of-biztalk-adapter-for-peoplesoft-enterprise/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: a277c5f5588a9455119b96f7c600dbadccffb8ac
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="peoplesoft-enterprise-requirements"></a><span data-ttu-id="0c480-101">PeopleSoft Enterprise 需求</span><span class="sxs-lookup"><span data-stu-id="0c480-101">PeopleSoft Enterprise Requirements</span></span>

## <a name="send-handler-requirements"></a><span data-ttu-id="0c480-102">傳送處理常式的需求</span><span class="sxs-lookup"><span data-stu-id="0c480-102">Send Handler requirements</span></span>  
 <span data-ttu-id="0c480-103">Microsoft BizTalk Adapter for PeopleSoft Enterprise 包含一個可供人透過 Java API 存取的自訂元件介面 (CI)。</span><span class="sxs-lookup"><span data-stu-id="0c480-103">Microsoft BizTalk Adapter for PeopleSoft Enterprise contains a custom component interface (CI) and provides access to it through a Java API.</span></span> <span data-ttu-id="0c480-104">將 `GET_CI_INFO` 這個自訂 CI 物件部署到 PeopleSoft 中 (以提供 BizTalk Adapter for PeopleSoft Enterprise 所需中繼資料資訊) 的方式，是透過 PeopleSoft 工具。</span><span class="sxs-lookup"><span data-stu-id="0c480-104">A custom CI object, `GET_CI_INFO`, is deployed in the PeopleSoft system using PeopleSoft Tools to provide metadata information that is required by BizTalk Adapter for PeopleSoft Enterprise.</span></span> <span data-ttu-id="0c480-105">如需詳細資訊，請參閱[安裝企業應用程式介面卡](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="0c480-105">For more information, see [Install Enterprise Applications adapters](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md).</span></span>  
  
 <span data-ttu-id="0c480-106">上傳自訂元件介面是只發生一次。</span><span class="sxs-lookup"><span data-stu-id="0c480-106">Uploading the custom component interface is a one-time occurrence.</span></span> <span data-ttu-id="0c480-107">`GET_CI_INFO.pc` 這個檔案會隨產品安裝，這個檔案必須要安裝好，您才能使用配接器瀏覽 CI。</span><span class="sxs-lookup"><span data-stu-id="0c480-107">This file, `GET_CI_INFO.pc`, installs with the product and must be installed before you can use the adapter to browse CIs.</span></span> <span data-ttu-id="0c480-108">您必須存取 PeopleSoft 應用程式設計工具。</span><span class="sxs-lookup"><span data-stu-id="0c480-108">You must have access to the PeopleSoft Application Designer.</span></span> <span data-ttu-id="0c480-109">在 BizTalk Server 電腦上沒有 Application Designer 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0c480-109">The Application Designer application does not have to be on the BizTalk Server computer.</span></span> <span data-ttu-id="0c480-110">您可以使用該 Application Designer 將自訂 CI 上傳到您瀏覽的 PeopleSoft 電腦。</span><span class="sxs-lookup"><span data-stu-id="0c480-110">You use the Application Designer to upload the custom CI onto the PeopleSoft computer that you browse.</span></span>  
  
 <span data-ttu-id="0c480-111">您必須有 PeopleSoft 電腦的存取權，因為您必須設定環境變數 CLASSPATH (或設定資訊**傳輸屬性**螢幕) 以指向 PeopleSoft 的`PSJOA/psjoa.jar`檔案。</span><span class="sxs-lookup"><span data-stu-id="0c480-111">You must have access to the PeopleSoft computer because you must set the environment variable CLASSPATH (or set the information in the **Transport Properties** screen) to point to PeopleSoft's `PSJOA/psjoa.jar` file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c480-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c480-112">See Also</span></span>  
 [<span data-ttu-id="0c480-113">快速入門</span><span class="sxs-lookup"><span data-stu-id="0c480-113">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-peoplesoft-enterprise.md)   
 