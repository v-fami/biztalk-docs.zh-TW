---
title: 開始使用 WCF LOB 配接器 sdk |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80b2d80b-9160-4569-821d-1e5c1338127d
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58f732ff26b42355937b1b44f2e571d91e64aadc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004095"
---
# <a name="get-started-with-the-with-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="e20a3-102">開始使用 WCF LOB 配接器 sdk</span><span class="sxs-lookup"><span data-stu-id="e20a3-102">Get started with the with the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="e20a3-103">本章節包含適用於不熟悉的使用者資訊[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e20a3-103">This section contains information that is relevant to users who are new to the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="e20a3-104">它包含有關安裝、 需要的技能和知識，一般開發人員工作、 可用社群資源和教學課程的主題。</span><span class="sxs-lookup"><span data-stu-id="e20a3-104">It contains topics about installation, required skills and knowledge, common developer tasks, available community resources, and tutorials.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="e20a3-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="e20a3-105">Prerequisites</span></span>

<span data-ttu-id="e20a3-106">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]適合需要整合的企業應用程式整合工作一部分的動態和複雜的業務系統的人員。</span><span class="sxs-lookup"><span data-stu-id="e20a3-106">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is intended for developers who need to integrate dynamic and complex line-of-business systems as part of an enterprise application integration effort.</span></span> <span data-ttu-id="e20a3-107">您可以下載最新版[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]位於[ http://go.microsoft.com/fwlink/?LinkID=189401 ](http://go.microsoft.com/fwlink/?LinkID=189401)。</span><span class="sxs-lookup"><span data-stu-id="e20a3-107">You can download the latest version of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] at [http://go.microsoft.com/fwlink/?LinkID=189401](http://go.microsoft.com/fwlink/?LinkID=189401).</span></span>  
  
 <span data-ttu-id="e20a3-108">若要建立的配接器使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，我們建議您在熟悉下列技術：</span><span class="sxs-lookup"><span data-stu-id="e20a3-108">To create an adapter using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], we suggest being experienced with the following technologies:</span></span>  
  
- [!INCLUDE[btsVStudioNet](../../includes/btsvstudionet-md.md)]<span data-ttu-id="e20a3-109"> 與.NET 解決方案開發</span><span class="sxs-lookup"><span data-stu-id="e20a3-109"> and the development of .NET solutions</span></span>  
  
- <span data-ttu-id="e20a3-110">.NET Framework 程式設計</span><span class="sxs-lookup"><span data-stu-id="e20a3-110">Programming with the .NET Framework</span></span>  
  
- [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]  
  
- <span data-ttu-id="e20a3-111">.NET XML 程式設計 API</span><span class="sxs-lookup"><span data-stu-id="e20a3-111">.NET XML Programming API</span></span>  
  
- <span data-ttu-id="e20a3-112">Web 服務描述語言 (WSDL) 和 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="e20a3-112">Web Service Description Language (WSDL) and XML Schema</span></span>  
  
  <span data-ttu-id="e20a3-113">您也應該要熟悉作業的目標系統，以及用來在目標系統 API 公開 （expose） 的技術。</span><span class="sxs-lookup"><span data-stu-id="e20a3-113">You should also be familiar with the operation of the target system as well as the technology used to expose the target system API.</span></span>    

  
## <a name="see-also"></a><span data-ttu-id="e20a3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e20a3-114">See Also</span></span>  
[<span data-ttu-id="e20a3-115">了解架構和 WCF LOB 配接器 SDK 的不同元件</span><span class="sxs-lookup"><span data-stu-id="e20a3-115">Understand the architecture and different components of the WCF LOB Adapter SDK</span></span>](understand-the-architecture-and-different-components-of-the-wcf-lob-adapter-sdk.md)