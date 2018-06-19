---
title: BTSWebSvcPub 命令列參照 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5e19dd4d-9f2c-4a17-9437-8701e1c274fb
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c9993092c0d798ae2d47f614a24da21c3a2df62
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22232854"
---
# <a name="btswebsvcpub-command-line-reference"></a><span data-ttu-id="f073e-102">BTSWebSvcPub 命令列參照</span><span class="sxs-lookup"><span data-stu-id="f073e-102">BTSWebSvcPub Command-Line Reference</span></span>
<span data-ttu-id="f073e-103">本主題提供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所附 BTSWebSvcPub 命令列工具的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="f073e-103">This topic provides reference information for the BTSWebSvcPub command-line tool included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="f073e-104">您可以使用 BTSWebSvcPub 建立 Web 服務 (.asmx) 以便透過該 Web 服務發佈協調流程，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f073e-104">You can use BTSWebSvcPub to create Web services (.asmx) for publishing orchestrations through Web services as follows:</span></span>  
  
## <a name="usage"></a><span data-ttu-id="f073e-105">使用方式</span><span class="sxs-lookup"><span data-stu-id="f073e-105">Usage</span></span>  
 <span data-ttu-id="f073e-106">**BTSWebSvcPub PathName [-位置︰** *值* **] [-覆寫] [-匿名]**</span><span class="sxs-lookup"><span data-stu-id="f073e-106">**BTSWebSvcPub PathName [-Location:** *value* **] [-Overwrite] [-Anonymous]**</span></span>  
  
 <span data-ttu-id="f073e-107">**[-名稱︰** *值* **] [-命名空間︰** *值* **] [-TargetNamespace:** *值* **]**</span><span class="sxs-lookup"><span data-stu-id="f073e-107">**[-Name:** *value* **] [-Namespace:** *value* **] [-TargetNamespace:** *value* **]**</span></span>  
  
 <span data-ttu-id="f073e-108">**[-UnknownHeaders [** *+* **&#124;** *-* **]][-SingleSignOn[** *+* **&#124;** *-* **]][-ParameterStyle:** *值* **]**</span><span class="sxs-lookup"><span data-stu-id="f073e-108">**[-UnknownHeaders[** *+* **&#124;** *-* **]] [-SingleSignOn[** *+* **&#124;** *-* **]] [-ParameterStyle:** *value* **]**</span></span>  
  
 <span data-ttu-id="f073e-109">**[-ConformanceClaims:** *值* **] [-ForceRequestResponse:** *值* **] [-ReceiveLocation]**</span><span class="sxs-lookup"><span data-stu-id="f073e-109">**[-ConformanceClaims:** *value* **] [-ForceRequestResponse:** *value* **] [-ReceiveLocation]**</span></span>  
  
 <span data-ttu-id="f073e-110">**[-ApplicationName:** *值* **]**</span><span class="sxs-lookup"><span data-stu-id="f073e-110">**[-ApplicationName:** *value* **]**</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="f073e-111">參數</span><span class="sxs-lookup"><span data-stu-id="f073e-111">Parameters</span></span>  
  
|<span data-ttu-id="f073e-112">參數</span><span class="sxs-lookup"><span data-stu-id="f073e-112">Parameter</span></span>|<span data-ttu-id="f073e-113">必要項</span><span class="sxs-lookup"><span data-stu-id="f073e-113">Required</span></span>|<span data-ttu-id="f073e-114">Description</span><span class="sxs-lookup"><span data-stu-id="f073e-114">Description</span></span>|  
|---------------|--------------|-----------------|  
|<span data-ttu-id="f073e-115">**路徑名稱**</span><span class="sxs-lookup"><span data-stu-id="f073e-115">**PathName**</span></span>|<span data-ttu-id="f073e-116">是</span><span class="sxs-lookup"><span data-stu-id="f073e-116">Yes</span></span>|<span data-ttu-id="f073e-117">BizTalk 組件 (*.dll) 或 web 服務描述的路徑和檔案名稱 (\*.xml) 檔案。</span><span class="sxs-lookup"><span data-stu-id="f073e-117">Path and file name of BizTalk assembly (*.dll) or web service description (\*.xml) file.</span></span>|  
|<span data-ttu-id="f073e-118">**位置**</span><span class="sxs-lookup"><span data-stu-id="f073e-118">**-Location**</span></span>|<span data-ttu-id="f073e-119">否</span><span class="sxs-lookup"><span data-stu-id="f073e-119">No</span></span>|<span data-ttu-id="f073e-120">要發佈的位置。</span><span class="sxs-lookup"><span data-stu-id="f073e-120">Location in which to publish.</span></span> <span data-ttu-id="f073e-121">(語法:"http://host[: 連接埠] / 路徑 」)</span><span class="sxs-lookup"><span data-stu-id="f073e-121">(Syntax:"http://host[:port]/path")</span></span>|  
|<span data-ttu-id="f073e-122">**-覆寫**</span><span class="sxs-lookup"><span data-stu-id="f073e-122">**-Overwrite**</span></span>|<span data-ttu-id="f073e-123">否</span><span class="sxs-lookup"><span data-stu-id="f073e-123">No</span></span>|<span data-ttu-id="f073e-124">覆寫指定的位置。</span><span class="sxs-lookup"><span data-stu-id="f073e-124">Overwrite specified location.</span></span>|  
|<span data-ttu-id="f073e-125">**匿名**</span><span class="sxs-lookup"><span data-stu-id="f073e-125">**-Anonymous**</span></span>|<span data-ttu-id="f073e-126">否</span><span class="sxs-lookup"><span data-stu-id="f073e-126">No</span></span>|<span data-ttu-id="f073e-127">允許匿名存取 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="f073e-127">Allow anonymous access to Web service.</span></span>|  
|<span data-ttu-id="f073e-128">**-名稱**</span><span class="sxs-lookup"><span data-stu-id="f073e-128">**-Name**</span></span>|<span data-ttu-id="f073e-129">否</span><span class="sxs-lookup"><span data-stu-id="f073e-129">No</span></span>|<span data-ttu-id="f073e-130">要包含 Web 服務的解決方案和組件的名稱 (.sln 和 .dll 檔案)。</span><span class="sxs-lookup"><span data-stu-id="f073e-130">Name of the solution and assembly (.sln and .dll files) that will contain the Web service.</span></span>|  
|<span data-ttu-id="f073e-131">**命名空間**</span><span class="sxs-lookup"><span data-stu-id="f073e-131">**-Namespace**</span></span>|<span data-ttu-id="f073e-132">否</span><span class="sxs-lookup"><span data-stu-id="f073e-132">No</span></span>|<span data-ttu-id="f073e-133">Web 服務代碼的預設命名空間。</span><span class="sxs-lookup"><span data-stu-id="f073e-133">Default namespace for Web service code.</span></span>|  
|<span data-ttu-id="f073e-134">**-目標命名空間**</span><span class="sxs-lookup"><span data-stu-id="f073e-134">**-Targetnamespace**</span></span>|<span data-ttu-id="f073e-135">否</span><span class="sxs-lookup"><span data-stu-id="f073e-135">No</span></span>|<span data-ttu-id="f073e-136">Web 服務的目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="f073e-136">Target namespace of the Web service.</span></span> <span data-ttu-id="f073e-137">(範例:'http://www.northwindtraders.com')</span><span class="sxs-lookup"><span data-stu-id="f073e-137">(Example:'http://www.northwindtraders.com')</span></span>|  
|<span data-ttu-id="f073e-138">**-UnknownHeaders**</span><span class="sxs-lookup"><span data-stu-id="f073e-138">**-UnknownHeaders**</span></span>|<span data-ttu-id="f073e-139">否</span><span class="sxs-lookup"><span data-stu-id="f073e-139">No</span></span>|<span data-ttu-id="f073e-140">支援未知 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="f073e-140">Support unknown SOAP headers.</span></span>|  
|<span data-ttu-id="f073e-141">**-SinglesSignon**</span><span class="sxs-lookup"><span data-stu-id="f073e-141">**-SinglesSignon**</span></span>|<span data-ttu-id="f073e-142">否</span><span class="sxs-lookup"><span data-stu-id="f073e-142">No</span></span>|<span data-ttu-id="f073e-143">支援 SharePoint Portal Server 單一登入 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="f073e-143">Support SharePoint Portal Server Single Sign-On SOAP headers.</span></span>|  
|<span data-ttu-id="f073e-144">**-ParameterStyle**</span><span class="sxs-lookup"><span data-stu-id="f073e-144">**-ParameterStyle**</span></span>|<span data-ttu-id="f073e-145">否</span><span class="sxs-lookup"><span data-stu-id="f073e-145">No</span></span>|<span data-ttu-id="f073e-146">訊息的 SoapParameterStyle:"Default"、"Bare"或"Wrapped"。</span><span class="sxs-lookup"><span data-stu-id="f073e-146">The SoapParameterStyle for messages: "Default", "Bare",or "Wrapped".</span></span>|  
|<span data-ttu-id="f073e-147">**-ConfirmanceClaims**</span><span class="sxs-lookup"><span data-stu-id="f073e-147">**-ConfirmanceClaims**</span></span>|<span data-ttu-id="f073e-148">否</span><span class="sxs-lookup"><span data-stu-id="f073e-148">No</span></span>|<span data-ttu-id="f073e-149">宣告 web 服務互通性 (WSI):"None"或"BasicProfile1_1"。</span><span class="sxs-lookup"><span data-stu-id="f073e-149">Web services interoperability (WSI) claim: "None" or"BasicProfile1_1".</span></span>|  
|<span data-ttu-id="f073e-150">**-ForceRequestResponse**</span><span class="sxs-lookup"><span data-stu-id="f073e-150">**-ForceRequestResponse**</span></span>|<span data-ttu-id="f073e-151">否</span><span class="sxs-lookup"><span data-stu-id="f073e-151">No</span></span>|<span data-ttu-id="f073e-152">公開單向 BizTalk 作業，做為要求-回應的 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="f073e-152">Expose one-way BizTalk operations as request-response web methods.</span></span>|  
|<span data-ttu-id="f073e-153">**-描述**</span><span class="sxs-lookup"><span data-stu-id="f073e-153">**-ReceiveLocation**</span></span>|<span data-ttu-id="f073e-154">否</span><span class="sxs-lookup"><span data-stu-id="f073e-154">No</span></span>|<span data-ttu-id="f073e-155">在指定的 BizTalk 應用程式中建立接收位置。</span><span class="sxs-lookup"><span data-stu-id="f073e-155">Create receive locations in the specified BizTalk application.</span></span>|  
|<span data-ttu-id="f073e-156">**-ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="f073e-156">**-ApplicationName**</span></span>|<span data-ttu-id="f073e-157">否</span><span class="sxs-lookup"><span data-stu-id="f073e-157">No</span></span>|<span data-ttu-id="f073e-158">要建立接收位置的 BizTalk 應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="f073e-158">Name of the BizTalk application in which to create receive locations.</span></span> <span data-ttu-id="f073e-159">若未指定，將使用預設的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f073e-159">If not specified, the default BizTalk application is used.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="f073e-160">範例</span><span class="sxs-lookup"><span data-stu-id="f073e-160">Sample</span></span>  
 <span data-ttu-id="f073e-161">BTSWebSvcPub.exe "MyAssembly.dll" -Location:http://localhost/MyVdir</span><span class="sxs-lookup"><span data-stu-id="f073e-161">BTSWebSvcPub.exe "MyAssembly.dll" -Location:http://localhost/MyVdir</span></span>  
  
 <span data-ttu-id="f073e-162">-Overwrite</span><span class="sxs-lookup"><span data-stu-id="f073e-162">-Overwrite</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f073e-163">備註</span><span class="sxs-lookup"><span data-stu-id="f073e-163">Remarks</span></span>  
 <span data-ttu-id="f073e-164">參數名稱不區分大小寫，而且可以縮寫。</span><span class="sxs-lookup"><span data-stu-id="f073e-164">Parameter names are not case sensitive and may be abbreviated.</span></span> <span data-ttu-id="f073e-165">參數值會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f073e-165">Parameter values are case sensitive.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f073e-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f073e-166">See Also</span></span>  
 [<span data-ttu-id="f073e-167">如何使用 BizTalk Web 服務發佈精靈發佈為 Web 服務的協調流程</span><span class="sxs-lookup"><span data-stu-id="f073e-167">How to Use the BizTalk Web Services Publishing Wizard to Publish an Orchestration as a Web Service</span></span>](../core/publish-orchestration-as-web-service--biztalk-web-services-publishing-wizard.md)