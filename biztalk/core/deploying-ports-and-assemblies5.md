---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-peoplesoft-enterprise/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: ed7dd37633fc308cccedf40b321f46bf4c2b8ea2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972063"
---
# <a name="deploying-ports-and-assemblies"></a><span data-ttu-id="0910d-101">部署連接埠和組件</span><span class="sxs-lookup"><span data-stu-id="0910d-101">Deploying Ports and Assemblies</span></span>
<span data-ttu-id="0910d-102">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在目標電腦上複製連接埠和組件。</span><span class="sxs-lookup"><span data-stu-id="0910d-102">Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0910d-103"> 傳送埠/接收位置將組態匯出到 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="0910d-103"> exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="0910d-104">您會使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="0910d-104">You use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to perform these tasks:</span></span>  
  
- <span data-ttu-id="0910d-105">在 BizTalk 組態資料庫中部署或移除 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件。</span><span class="sxs-lookup"><span data-stu-id="0910d-105">Deploy or remove [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies in a BizTalk Configuration database.</span></span>  
  
- <span data-ttu-id="0910d-106">在全域組件快取 (GAC) 中安裝或解除安裝組件。</span><span class="sxs-lookup"><span data-stu-id="0910d-106">Install or uninstall the assemblies in the global assembly cache (GAC).</span></span>  
  
- <span data-ttu-id="0910d-107">將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件繫結資訊匯入到繫結檔案，或是將它從繫結檔案中匯出。</span><span class="sxs-lookup"><span data-stu-id="0910d-107">Import or export [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assembly binding information to and from binding files.</span></span>  
  
  <span data-ttu-id="0910d-108">如需有關如何使用資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]若要將連接埠和組件的部署，請參閱[如何匯出 BizTalk 應用程式的繫結](../core/how-to-export-bindings-for-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="0910d-108">For information about how to use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0910d-109">Microsoft BizTalk Adapter for PeopleSoft Enterprise 只要求來源 (開發) 電腦上必須有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="0910d-109">The Microsoft BizTalk Adapter for PeopleSoft Enterprise only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="0910d-110">實際執行電腦上不需要有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="0910d-110">Visual Studio is not required on the production computer.</span></span>  
  
