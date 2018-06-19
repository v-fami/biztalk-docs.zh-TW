---
title: 開發 BizTalk Server 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 99b56f86-d8e4-4f4a-9ce9-9f476ba88ea8
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c71782556d896d0697b73b83e2966f304b77a3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239598"
---
# <a name="developing-biztalk-server-applications"></a><span data-ttu-id="17251-102">開發 BizTalk Server 應用程式</span><span class="sxs-lookup"><span data-stu-id="17251-102">Developing BizTalk Server Applications</span></span>
<span data-ttu-id="17251-103">本節包含的資訊可供負責建立 BizTalk 專案的開發人員使用。</span><span class="sxs-lookup"><span data-stu-id="17251-103">This section contains information for developers who are tasked with creating BizTalk projects.</span></span> <span data-ttu-id="17251-104">專案是使用 BizTalk 專案系統設計環境建立的，可用以設計、組織和建置 BizTalk 應用程式的各種項目。</span><span class="sxs-lookup"><span data-stu-id="17251-104">Projects are created using the BizTalk project System Design Environment, which allows you to design, organize, and build the various elements of BizTalk applications.</span></span> <span data-ttu-id="17251-105">以下各節詳細描述此程序。</span><span class="sxs-lookup"><span data-stu-id="17251-105">The following sections describe this process in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17251-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="17251-106">In This Section</span></span>  
  
-   [<span data-ttu-id="17251-107">開發人員工具</span><span class="sxs-lookup"><span data-stu-id="17251-107">Developer Tools</span></span>](../core/developer-tools.md)  
  
-   [<span data-ttu-id="17251-108">使用 「 BizTalk 傳訊引擎</span><span class="sxs-lookup"><span data-stu-id="17251-108">Using the BizTalk Messaging Engine</span></span>](../core/using-the-biztalk-messaging-engine.md)  
  
-   [<span data-ttu-id="17251-109">使用 BizTalk 編輯器建立結構描述</span><span class="sxs-lookup"><span data-stu-id="17251-109">Creating Schemas Using BizTalk Editor</span></span>](../core/creating-schemas-using-biztalk-editor.md)  
  
-   [<span data-ttu-id="17251-110">使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="17251-110">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)  
  
-   [<span data-ttu-id="17251-111">建立管線使用管線設計師</span><span class="sxs-lookup"><span data-stu-id="17251-111">Creating Pipelines Using Pipeline Designer</span></span>](../core/creating-pipelines-using-pipeline-designer.md)  
  
-   [<span data-ttu-id="17251-112">建立協調流程使用協調流程設計師</span><span class="sxs-lookup"><span data-stu-id="17251-112">Creating Orchestrations Using Orchestration Designer</span></span>](../core/creating-orchestrations-using-orchestration-designer.md)  
  
-   [<span data-ttu-id="17251-113">建立和使用商務規則</span><span class="sxs-lookup"><span data-stu-id="17251-113">Creating and Using Business Rules</span></span>](../core/creating-and-using-business-rules.md)  
  
-   [<span data-ttu-id="17251-114">使用 Web 服務</span><span class="sxs-lookup"><span data-stu-id="17251-114">Using Web Services</span></span>](../core/using-web-services.md)  
  
-   [<span data-ttu-id="17251-115">使用 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="17251-115">Using WCF Services</span></span>](../core/using-wcf-services.md)  
  
-   [<span data-ttu-id="17251-116">設計 BizTalk 應用程式的國際化考量</span><span class="sxs-lookup"><span data-stu-id="17251-116">International Considerations for Designing BizTalk Applications</span></span>](../core/international-considerations-for-designing-biztalk-applications.md)  
  
-   [<span data-ttu-id="17251-117">部署 BizTalk 組件從 Visual Studio 到 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="17251-117">Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application</span></span>](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)  
  
-   [<span data-ttu-id="17251-118">建立單一登入應用程式</span><span class="sxs-lookup"><span data-stu-id="17251-118">Creating a Single Sign-On Application</span></span>](../core/creating-a-single-sign-on-application.md)  
  
-   [<span data-ttu-id="17251-119">檢視 BizTalk 組件檢視器的組件</span><span class="sxs-lookup"><span data-stu-id="17251-119">Viewing Assemblies with the BizTalk Assembly Viewer</span></span>](../core/viewing-assemblies-with-the-biztalk-assembly-viewer.md)  
  
-   [<span data-ttu-id="17251-120">實作訊息安全性</span><span class="sxs-lookup"><span data-stu-id="17251-120">Implementing Message Security</span></span>](../core/implementing-message-security.md)  
  
## <a name="see-also"></a><span data-ttu-id="17251-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17251-121">See Also</span></span>  
 <span data-ttu-id="17251-122">[了解 BizTalk 應用程式部署和管理](../core/understanding-biztalk-application-deployment-and-management.md) </span><span class="sxs-lookup"><span data-stu-id="17251-122">[Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md) </span></span>  
 <span data-ttu-id="17251-123">[BizTalk 應用程式部署和管理檢查清單](../core/biztalk-application-deployment-and-management-checklists.md) </span><span class="sxs-lookup"><span data-stu-id="17251-123">[BizTalk Application Deployment and Management Checklists](../core/biztalk-application-deployment-and-management-checklists.md) </span></span>  
 [<span data-ttu-id="17251-124">BizTalk 應用程式部署和管理逐步解說</span><span class="sxs-lookup"><span data-stu-id="17251-124">BizTalk Application Deployment and Management Walkthroughs</span></span>](http://msdn.microsoft.com/library/5321f8e0-1e2a-4ac4-a4a2-fc244071bc5b)