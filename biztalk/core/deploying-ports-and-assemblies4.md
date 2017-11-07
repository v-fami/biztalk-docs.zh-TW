---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: ac85aec2f1153d5117c95627e573ec563d58dbc2
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="deploying-ports-and-assemblies"></a><span data-ttu-id="332fc-101">部署連接埠和組件</span><span class="sxs-lookup"><span data-stu-id="332fc-101">Deploying Ports and Assemblies</span></span>
<span data-ttu-id="332fc-102">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在目標電腦上複製連接埠和組件。</span><span class="sxs-lookup"><span data-stu-id="332fc-102">Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> <span data-ttu-id="332fc-103">BizTalk Server 會將傳送埠/接收位置組態匯出到 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="332fc-103">BizTalk Server exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="332fc-104">您可以使用 BizTalk Server 執行以下工作：</span><span class="sxs-lookup"><span data-stu-id="332fc-104">You can use BizTalk Server to do the following tasks:</span></span>  
  
-   <span data-ttu-id="332fc-105">在 BizTalk 組態資料庫中部署或移除 BizTalk Server 組件</span><span class="sxs-lookup"><span data-stu-id="332fc-105">Deploy or remove BizTalk Server assemblies in a BizTalk Configuration database</span></span>  
  
-   <span data-ttu-id="332fc-106">在全域組件快取 (GAC) 中安裝或解除安裝組件</span><span class="sxs-lookup"><span data-stu-id="332fc-106">Install or uninstall the assemblies in the global assembly cache (GAC)</span></span>  
  
-   <span data-ttu-id="332fc-107">將 BizTalk Server 組件繫結資訊匯入到繫結檔案，或是將它從繫結檔案中匯出</span><span class="sxs-lookup"><span data-stu-id="332fc-107">Import or export BizTalk Server assembly binding information to and from binding files</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="332fc-108">Microsoft BizTalk Adapter for JD Edwards OneWorld 只要求來源 (部署) 電腦上必須有 Visual Studio；</span><span class="sxs-lookup"><span data-stu-id="332fc-108">The Microsoft BizTalk Adapter for JD Edwards OneWorld only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="332fc-109">實際執行電腦上不需要有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="332fc-109">Visual Studio is not required on the production computer.</span></span>  
  
