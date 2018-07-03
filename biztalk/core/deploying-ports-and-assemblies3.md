---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: d2989e2e638a4d7f5c1fc56935578b04d75acfa0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986271"
---
# <a name="deploying-ports-and-assemblies"></a><span data-ttu-id="d8a84-101">部署連接埠和組件</span><span class="sxs-lookup"><span data-stu-id="d8a84-101">Deploying Ports and Assemblies</span></span>
<span data-ttu-id="d8a84-102">使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您可以複製連接埠和組件的目標電腦上。</span><span class="sxs-lookup"><span data-stu-id="d8a84-102">With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d8a84-103"> 傳送埠/接收位置將組態匯出到 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="d8a84-103"> exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="d8a84-104">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d8a84-104">You can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to do the following tasks:</span></span>  
  
- <span data-ttu-id="d8a84-105">在 BizTalk 組態資料庫中部署或移除 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件</span><span class="sxs-lookup"><span data-stu-id="d8a84-105">Deploy or remove [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies in a BizTalk Configuration database</span></span>  
  
- <span data-ttu-id="d8a84-106">在全域組件快取 (GAC) 中安裝或解除安裝組件</span><span class="sxs-lookup"><span data-stu-id="d8a84-106">Install or uninstall the assemblies in the global assembly cache (GAC)</span></span>  
  
- <span data-ttu-id="d8a84-107">將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件繫結資訊匯入到繫結檔案，或是將之從繫結檔案中匯出</span><span class="sxs-lookup"><span data-stu-id="d8a84-107">Import or export [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assembly binding information to and from binding files</span></span>  
  
  <span data-ttu-id="d8a84-108">如需有關如何使用資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]若要將連接埠和組件的部署，請參閱[如何匯出 BizTalk 應用程式的繫結](../core/how-to-export-bindings-for-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="d8a84-108">For information about how to use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8a84-109">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 只要求來源 (程式開發) 電腦上必須有 Visual Studio；</span><span class="sxs-lookup"><span data-stu-id="d8a84-109">The Microsoft BizTalk Adapter for JD Edwards EnterpriseOne only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="d8a84-110">實際執行電腦上不需要有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d8a84-110">Visual Studio is not required on the production computer.</span></span>  
  
