---
title: "如何設定已安裝的 Web 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, configuring
- deploying, Web services
- Web services, deploying
ms.assetid: 5a281daa-9e1c-47b0-9002-66ea18ed6caf
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f54d5fd99bfa9f5a7440202848c4d43259d0a42
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-installed-web-service"></a><span data-ttu-id="65e35-102">如何設定已安裝的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="65e35-102">How to Configure the Installed Web Service</span></span>
<span data-ttu-id="65e35-103">安裝 Web 服務檔案之後，您必須設定 BizTalk Server 從 Web 服務接收訊息。</span><span class="sxs-lookup"><span data-stu-id="65e35-103">After you install the Web service files, you must configure BizTalk Server to receive messages from the Web service.</span></span>  
  
### <a name="to-configure-the-web-service"></a><span data-ttu-id="65e35-104">若要設定 Web 服務</span><span class="sxs-lookup"><span data-stu-id="65e35-104">To configure the Web service</span></span>  
  
1.  <span data-ttu-id="65e35-105">在 BizTalk Server 管理主控台中，展開  **BizTalk 群組**，依序展開**應用程式**，然後以滑鼠右鍵按一下您想要設定 Web 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="65e35-105">In BizTalk Server Administration console, expand **BizTalk Group**, expand **Applications**, and then right-click the application that you want to configure the Web Service.</span></span>  
  
2.  <span data-ttu-id="65e35-106">指向**匯入**，然後按一下 **繫結**。</span><span class="sxs-lookup"><span data-stu-id="65e35-106">Point to **Import**, and then click **Bindings**.</span></span>  
  
3.  <span data-ttu-id="65e35-107">在 [發佈] 資料夾中，選取 BindingInfo.xml 檔案，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="65e35-107">Select the BindingInfo.xml file in the distribution folder, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="65e35-108">啟動協調流程並啟用接收位置。</span><span class="sxs-lookup"><span data-stu-id="65e35-108">Start your orchestrations and enable receive locations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65e35-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65e35-109">See Also</span></span>  
 <span data-ttu-id="65e35-110">[如何將繫結匯入到 BizTalk 應用程式](../core/how-to-import-bindings-into-a-biztalk-application.md) </span><span class="sxs-lookup"><span data-stu-id="65e35-110">[How to Import Bindings into a BizTalk Application](../core/how-to-import-bindings-into-a-biztalk-application.md) </span></span>  
 [<span data-ttu-id="65e35-111">部署在非 Visual Studio 電腦上的已發佈的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="65e35-111">Deploying Published Web Services on a Non-Visual Studio Computer</span></span>](../core/deploying-published-web-services-on-a-non-visual-studio-computer.md)