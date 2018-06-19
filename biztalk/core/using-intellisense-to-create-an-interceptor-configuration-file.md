---
title: 使用 IntelliSense 建立攔截器組態檔 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 349ea1bf-a5d1-4464-bf4b-d8746c622377
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7be3f79545db81a0127fc8d004d71c758069a55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287966"
---
# <a name="using-intellisense-to-create-an-interceptor-configuration-file"></a><span data-ttu-id="729fc-102">使用 IntelliSense 建立攔截器組態檔</span><span class="sxs-lookup"><span data-stu-id="729fc-102">Using IntelliSense to Create an Interceptor Configuration File</span></span>
<span data-ttu-id="729fc-103">您可以使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中的 IntelliSense 和結構描述驗證，協助您建構結構描述上有效的攔截器組態檔。</span><span class="sxs-lookup"><span data-stu-id="729fc-103">You can use IntelliSense and schema validation in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to help you construct interceptor configuration files that are schematically valid.</span></span> <span data-ttu-id="729fc-104">BAM 管理公用程式會對照基本攔截器組態結構描述驗證您的攔截器組態檔，而且如果檔案無效，則不會部署結構描述。</span><span class="sxs-lookup"><span data-stu-id="729fc-104">The BAM management utility validates your interceptor configuration file against the base interceptor configuration schema and, if the file is not valid, does not deploy the schema.</span></span> <span data-ttu-id="729fc-105">如果檔案通過基本攔截器組態結構描述的驗證，則會在執行階段對照技術專屬結構描述 (如 [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] 結構描述或 [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] 結構描述) 進行驗證，而如果發生錯誤，則不會進行攔截。</span><span class="sxs-lookup"><span data-stu-id="729fc-105">If the file passes validation against the base interceptor configuration schema, it is validated against technology-specific schemas like the [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] schema or the [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] schema during run time and if errors are encountered, no interception will occur.</span></span> <span data-ttu-id="729fc-106">您可以在建構攔截器組態檔時，使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中的結構描述驗證來避開這些錯誤。</span><span class="sxs-lookup"><span data-stu-id="729fc-106">You can avoid these errors by using schema validation in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] when constructing your interceptor configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="729fc-107">範例 BAM 攔截器組態 XSD 檔會隨 SDK 檔一併安裝。</span><span class="sxs-lookup"><span data-stu-id="729fc-107">The sample BAM interceptor configuration XSD files are installed with the SDK files.</span></span> <span data-ttu-id="729fc-108">檔案位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\BAM\InterceptorXSDs：</span><span class="sxs-lookup"><span data-stu-id="729fc-108">They can be found at [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\BAM\InterceptorXSDs:</span></span>  
>   
>  -   <span data-ttu-id="729fc-109">CommonInterceptorConfiguration.xsd</span><span class="sxs-lookup"><span data-stu-id="729fc-109">CommonInterceptorConfiguration.xsd</span></span>  
> -   <span data-ttu-id="729fc-110">WcfInterceptorConfiguration.xsd</span><span class="sxs-lookup"><span data-stu-id="729fc-110">WcfInterceptorConfiguration.xsd</span></span>  
> -   <span data-ttu-id="729fc-111">WorkflowInterceptorConfiguration.xsd</span><span class="sxs-lookup"><span data-stu-id="729fc-111">WorkflowInterceptorConfiguration.xsd</span></span>  
  
### <a name="to-obtain-a-copy-of-the-interceptor-schemas"></a><span data-ttu-id="729fc-112">取得攔截器結構描述的副本</span><span class="sxs-lookup"><span data-stu-id="729fc-112">To obtain a copy of the interceptor schemas</span></span>  
  
1.  <span data-ttu-id="729fc-113">開啟「記事本」或其他文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="729fc-113">Open Notepad or another text editor.</span></span>  
  
2.  <span data-ttu-id="729fc-114">瀏覽至[攔截器組態結構描述](../core/interceptor-configuration-schema.md)主題。</span><span class="sxs-lookup"><span data-stu-id="729fc-114">Navigate to the [Interceptor Configuration Schema](../core/interceptor-configuration-schema.md) topic.</span></span>  
  
3.  <span data-ttu-id="729fc-115">內容貼到新的文件中，開啟文字編輯器，然後將檔案儲存為文字檔，使用名稱**CommonInterceptorConfiguration.xsd** （或您自己選擇的其中一個） 至硬碟。</span><span class="sxs-lookup"><span data-stu-id="729fc-115">Paste the contents into a new document in the open text editor, and then save the file as a text file using the name **CommonInterceptorConfiguration.xsd** (or one of your own choosing) to your hard disk.</span></span>  
  
4.  <span data-ttu-id="729fc-116">重複這些步驟[!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)]結構描述和[!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)]使用檔案名稱的結構描述主題**WorkflowInterceptorConfiguration.xsd**和**WcfInterceptorConfiguration.xsd**或名稱您自己的選擇。</span><span class="sxs-lookup"><span data-stu-id="729fc-116">Repeat these steps for the [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] schema and [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] schema topics using the file names **WorkflowInterceptorConfiguration.xsd** and **WcfInterceptorConfiguration.xsd** or names of your own choosing.</span></span>  
  
### <a name="to-use-intellisense-with-your-interceptor-configuration-file"></a><span data-ttu-id="729fc-117">搭配攔截器組態檔使用 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="729fc-117">To use IntelliSense with your interceptor configuration file</span></span>  
  
1.  <span data-ttu-id="729fc-118">開啟 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="729fc-118">Open [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="729fc-119">按一下**檔案**，按一下 **新增**，然後按一下 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="729fc-119">Click **File**, click **New**, and then click **File**.</span></span>  
  
3.  <span data-ttu-id="729fc-120">在**新檔案**對話方塊中，選取**XML 檔案**，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="729fc-120">In the **New File** dialog box, select **XML File** and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="729fc-121">檢視 [屬性] 窗格，以滑鼠右鍵按一下 [編輯] 窗格中，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="729fc-121">View the Properties pane by right-clicking the edit pane, and then clicking **Properties**.</span></span>  
  
5.  <span data-ttu-id="729fc-122">在 [屬性] 窗格中，按一下**結構描述**，然後按一下省略符號 (**...**).</span><span class="sxs-lookup"><span data-stu-id="729fc-122">In the Properties pane, click **Schemas**, and then click the ellipsis (**…**).</span></span>  
  
6.  <span data-ttu-id="729fc-123">在**XML 結構描述**對話方塊中，按一下 **新增**然後瀏覽至該結構描述，然後選取位置**CommonInterceptorConfiguration.xsd**和**WcfInterceptorConfiguration.xsd**如果您正在使用[!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)]攔截器組態檔，或**WorkflowInterceptorConfiguration.xsd**如果您正在使用[!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)]攔截器組態檔。</span><span class="sxs-lookup"><span data-stu-id="729fc-123">In the **XML Schemas** dialog box, click **Add** and then navigate to the location of the schemas and select **CommonInterceptorConfiguration.xsd** and **WcfInterceptorConfiguration.xsd** if you are working with a [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] interceptor configuration file, or **WorkflowInterceptorConfiguration.xsd** if you are working with a [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] interceptor configuration file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="729fc-124">如果您使用不同的名稱儲存檔案，則選取這些檔案。</span><span class="sxs-lookup"><span data-stu-id="729fc-124">If you saved the files using different names, select those files instead.</span></span>  
  
7.  <span data-ttu-id="729fc-125">現在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 會在攔截器組態檔開啟時進行驗證，並且提供 IntelliSense 協助您建立和修改檔案。</span><span class="sxs-lookup"><span data-stu-id="729fc-125">[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] will now validate your interceptor configuration file when it is opened and supply IntelliSense help as you create and modify the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="729fc-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="729fc-126">See Also</span></span>  
 <span data-ttu-id="729fc-127">[Windows Workflow Foundation 結構描述](../core/windows-workflow-foundation-schema.md) </span><span class="sxs-lookup"><span data-stu-id="729fc-127">[Windows Workflow Foundation Schema](../core/windows-workflow-foundation-schema.md) </span></span>  
 [<span data-ttu-id="729fc-128">Windows Communication Foundation 結構描述</span><span class="sxs-lookup"><span data-stu-id="729fc-128">Windows Communication Foundation Schema</span></span>](../core/windows-communication-foundation-schema.md)