---
title: 建立應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b6e325c-a86f-419d-9a27-864f4f035507
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 772ba15d357715d5ceeca3c229167a96f7ef6c60
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987543"
---
# <a name="creating-an-application"></a><span data-ttu-id="22a8b-102">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="22a8b-102">Creating an Application</span></span>
<span data-ttu-id="22a8b-103">有三種方式可建立 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="22a8b-103">There are three ways to create a BizTalk application.</span></span> <span data-ttu-id="22a8b-104">另外還有幾個選項命名、 參考及部署應用程式的成品。</span><span class="sxs-lookup"><span data-stu-id="22a8b-104">There are also several options for naming, referencing, and deploying artifacts to applications.</span></span>  
  
## <a name="creating-a-biztalk-application"></a><span data-ttu-id="22a8b-105">建立 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="22a8b-105">Creating a BizTalk Application</span></span>  
 <span data-ttu-id="22a8b-106">三種方式如下所示：</span><span class="sxs-lookup"><span data-stu-id="22a8b-106">The three ways are as follows:</span></span>  
  
1. <span data-ttu-id="22a8b-107">使用 BizTalk Server 管理主控台的 [新增應用程式] 命令或 BTSTask 命令列工具的 AddApp 命令，建立 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="22a8b-107">Create the BizTalk application by using the New Application command of the BizTalk Server Administration console or the AddApp command of the BTSTask command-line tool.</span></span> <span data-ttu-id="22a8b-108">如需使用這些命令的詳細資訊，請參閱 <<c0> [ 如何建立應用程式](http://go.microsoft.com/fwlink/?LinkId=155007)(http://go.microsoft.com/fwlink/?LinkId=155007)。</span><span class="sxs-lookup"><span data-stu-id="22a8b-108">For more information about using these commands, see [How to Create an Application](http://go.microsoft.com/fwlink/?LinkId=155007) (http://go.microsoft.com/fwlink/?LinkId=155007).</span></span>  
  
2. <span data-ttu-id="22a8b-109">匯入已經從另一個應用程式匯出的 .msi 檔案。</span><span class="sxs-lookup"><span data-stu-id="22a8b-109">Import an .msi file that was exported from another application.</span></span> <span data-ttu-id="22a8b-110">如果目前 BizTalk 群組中沒有此應用程式，則會在目前 BizTalk 群組中自動建立此應用程式以及它的成品。</span><span class="sxs-lookup"><span data-stu-id="22a8b-110">If the application does not already exist in the current BizTalk group, the application, including its artifacts, is automatically created in the current BizTalk group.</span></span> <span data-ttu-id="22a8b-111">如需有關如何匯入應用程式的詳細資訊，請參閱 <<c0> [ 如何匯入 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154827)(http://go.microsoft.com/fwlink/?LinkID=154827)。</span><span class="sxs-lookup"><span data-stu-id="22a8b-111">For more information about importing applications, see [How to Import a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154827) (http://go.microsoft.com/fwlink/?LinkID=154827).</span></span>  
  
3. <span data-ttu-id="22a8b-112">從 Visual Studio 將 BizTalk 組件部署到 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="22a8b-112">Deploy BizTalk assemblies from Visual Studio into a BizTalk application.</span></span> <span data-ttu-id="22a8b-113">如果在 Visual Studio 中專案的部署屬性中指定的應用程式不存在於目前的 BizTalk 群組中，將會自動予以建立。</span><span class="sxs-lookup"><span data-stu-id="22a8b-113">If the application specified in the deployment properties for a project in Visual Studio does not exist in the current BizTalk group, it will be automatically created.</span></span> <span data-ttu-id="22a8b-114">如需部署組件從 Visual Studio 的詳細資訊，請參閱[從 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](http://go.microsoft.com/fwlink/?LinkID=154719)(http://go.microsoft.com/fwlink/?LinkID=154719)。</span><span class="sxs-lookup"><span data-stu-id="22a8b-114">For more information about deploying an assembly from Visual Studio, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154719) (http://go.microsoft.com/fwlink/?LinkID=154719).</span></span>  
  
   <span data-ttu-id="22a8b-115">若要部署應用程式使用.msi 檔，目的地應用程式不需要存在，但將會自動建立。</span><span class="sxs-lookup"><span data-stu-id="22a8b-115">To deploy an application using an .msi file, the destination application does not need to exist, but will be automatically created.</span></span> <span data-ttu-id="22a8b-116">不過，將繫結匯入到另一個應用程式，接收端應用程式必須存在。</span><span class="sxs-lookup"><span data-stu-id="22a8b-116">However, to import bindings from one application to another, the destination application must already exist.</span></span> <span data-ttu-id="22a8b-117">如果沒有，您需要建立藉由執行其中一個上面所列的程序。</span><span class="sxs-lookup"><span data-stu-id="22a8b-117">If not, you need to create it by performing one of the procedures listed above.</span></span>  
  
   <span data-ttu-id="22a8b-118">如需有關建立應用程式所需的特定步驟的詳細資訊，請參閱 <<c0> [ 如何建立應用程式](http://go.microsoft.com/fwlink/?LinkId=155007)(http://go.microsoft.com/fwlink/?LinkId=155007)。</span><span class="sxs-lookup"><span data-stu-id="22a8b-118">For more information about the specific steps required to create an application, see [How to Create an Application](http://go.microsoft.com/fwlink/?LinkId=155007) (http://go.microsoft.com/fwlink/?LinkId=155007).</span></span>  
  
## <a name="application-options"></a><span data-ttu-id="22a8b-119">應用程式選項</span><span class="sxs-lookup"><span data-stu-id="22a8b-119">Application Options</span></span>  
 <span data-ttu-id="22a8b-120">然後再建立新的應用程式，您應該執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="22a8b-120">Before creating a new application, you should do the following:</span></span>  
  
-   <span data-ttu-id="22a8b-121">判斷應用程式的 BizTalk 群組內是唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="22a8b-121">Determine a name that is unique within the BizTalk group for the application.</span></span>  
  
-   <span data-ttu-id="22a8b-122">將參考加入新的應用程式，以包含您想要在新的應用程式中重複使用的成品的任何應用程式。</span><span class="sxs-lookup"><span data-stu-id="22a8b-122">Add a reference from the new application to any application containing artifacts that you want to reuse in the new application.</span></span> <span data-ttu-id="22a8b-123">如需應用程式之間的相依性的詳細資訊，請參閱[相依性和應用程式部署](http://go.microsoft.com/fwlink/?LinkId=155008)(http://go.microsoft.com/fwlink/?LinkId=155008)。</span><span class="sxs-lookup"><span data-stu-id="22a8b-123">For more information about dependencies between applications, see [Dependencies and Application Deployment](http://go.microsoft.com/fwlink/?LinkId=155008) (http://go.microsoft.com/fwlink/?LinkId=155008).</span></span>  
  
-   <span data-ttu-id="22a8b-124">決定是否要將一些成品部署到個別的應用程式，例如，共用的成品應部署到他們自己個別的應用程式。</span><span class="sxs-lookup"><span data-stu-id="22a8b-124">Determine whether you want to deploy some artifacts into separate applications, for example, shared artifacts that should be deployed into their own separate application.</span></span>