---
title: 匯出 BizTalk 應用程式、 繫結和原則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- policies, exporting
- exporting, policies
- bindings, exporting
- exporting, applications
- applications, exporting
- exporting, bindings
ms.assetid: ac101206-be49-47c9-a354-4f39e8b77acf
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d6df445b0fefc132940a736870d66c62329ce60
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245806"
---
# <a name="exporting-biztalk-applications-bindings-and-policies"></a><span data-ttu-id="5fd04-102">匯出 BizTalk 應用程式、繫結和原則</span><span class="sxs-lookup"><span data-stu-id="5fd04-102">Exporting BizTalk Applications, Bindings, and Policies</span></span>
<span data-ttu-id="5fd04-103">本章節描述如何匯出 BizTalk 應用程式、繫結或原則。</span><span class="sxs-lookup"><span data-stu-id="5fd04-103">This section describes how to export a BizTalk application, bindings, or policies.</span></span> <span data-ttu-id="5fd04-104">您可以匯出 BizTalk 應用程式中所包含的部分或全部成品，也可以只匯出它的繫結或原則。</span><span class="sxs-lookup"><span data-stu-id="5fd04-104">You can export some or all of the artifacts contained in a BizTalk application, or you can export only its bindings or policies.</span></span> <span data-ttu-id="5fd04-105">匯出 BizTalk 應用程式會建立一個 Windows Installer (.msi) 檔案，此檔案包含您選取要匯出的應用程式成品。</span><span class="sxs-lookup"><span data-stu-id="5fd04-105">Exporting an application creates a Windows Installer (.msi) file containing the application artifacts that you selected for export.</span></span> <span data-ttu-id="5fd04-106">匯出繫結或原則會建立一個 .xml 檔案，其中包含這些繫結或原則。</span><span class="sxs-lookup"><span data-stu-id="5fd04-106">Exporting bindings or policies creates an .xml file of the bindings or policies.</span></span> <span data-ttu-id="5fd04-107">如需這個程序的背景資訊，請參閱[什麼發生時匯出成品](../core/what-happens-when-artifacts-are-exported.md)。</span><span class="sxs-lookup"><span data-stu-id="5fd04-107">For background information on this process, see [What Happens When Artifacts Are Exported](../core/what-happens-when-artifacts-are-exported.md).</span></span>  
  
 <span data-ttu-id="5fd04-108">您可以將應用程式 .msi 檔案匯入其他 BizTalk 群組中，以便在該群組中建立一個新的應用程式，使其包含該應用程式的成品。</span><span class="sxs-lookup"><span data-stu-id="5fd04-108">You can import an application .msi file into another BizTalk group to create a new application that contains the application's artifacts in that group.</span></span> <span data-ttu-id="5fd04-109">您可以將繫結或原則 .xml 檔案匯入另一個要使用這些繫結或原則的 BizTalk 應用程式中。</span><span class="sxs-lookup"><span data-stu-id="5fd04-109">You can import a binding or policy .xml file into another BizTalk application to use the bindings or policies.</span></span> <span data-ttu-id="5fd04-110">說明如何匯入成品[匯入 BizTalk 應用程式、 繫結和原則](../core/importing-biztalk-applications-bindings-and-policies.md)。</span><span class="sxs-lookup"><span data-stu-id="5fd04-110">How to import artifacts is described in [Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5fd04-111">請將繫結檔案儲存在安全的位置，因為這類檔案可能包含重要的商業資料 (如連線和組態資訊)。</span><span class="sxs-lookup"><span data-stu-id="5fd04-111">Store binding files in a secure location, as they may contain critical business data such as connectivity and configuration information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5fd04-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="5fd04-112">In This Section</span></span>  
  
-   [<span data-ttu-id="5fd04-113">如何匯出 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="5fd04-113">How to Export a BizTalk Application</span></span>](../core/how-to-export-a-biztalk-application.md)  
  
-   [<span data-ttu-id="5fd04-114">匯出繫結</span><span class="sxs-lookup"><span data-stu-id="5fd04-114">Exporting Bindings</span></span>](../core/exporting-bindings6.md)  
  
-   [<span data-ttu-id="5fd04-115">如何匯出原則</span><span class="sxs-lookup"><span data-stu-id="5fd04-115">How to Export a Policy</span></span>](../core/how-to-export-a-policy.md)