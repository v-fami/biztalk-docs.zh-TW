---
title: 環境變數如何指示部署狀態 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scripts, variables
ms.assetid: 022b782b-008d-41a7-9880-d1c4e5e4015e
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d21baa6ef6e6d82fc179497b4993cf3af6fb1a5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983983"
---
# <a name="how-environment-variables-indicate-deployment-state"></a><span data-ttu-id="3dba2-102">環境變數如何指示部署狀態</span><span class="sxs-lookup"><span data-stu-id="3dba2-102">How Environment Variables Indicate Deployment State</span></span>
<span data-ttu-id="3dba2-103">前置或後置處理指令碼一旦被叫用，便會檢查環境變數 BTAD_ChangeRequestAction、BTAD_InstallMode 與 BTAD_HostClass 以判斷目前所處的部署狀態 (安裝、匯入、刪除、解除安裝、匯入回復，或者安裝回復)。</span><span class="sxs-lookup"><span data-stu-id="3dba2-103">Once invoked, a pre- or post-processing script can determine in which deployment state (install, import, delete, uninstall, import rollback, or install rollback) it is running by checking the environment variables BTAD_ChangeRequestAction, BTAD_InstallMode and BTAD_HostClass.</span></span>  

 <span data-ttu-id="3dba2-104">下表描述三個指示不同部署狀態之變數的組合。</span><span class="sxs-lookup"><span data-stu-id="3dba2-104">The following table describes the combinations of the three variables that indicate the different deployment states.</span></span>  


|       <span data-ttu-id="3dba2-105">部署狀態</span><span class="sxs-lookup"><span data-stu-id="3dba2-105">Deployment State</span></span>        |     <span data-ttu-id="3dba2-106">預期值</span><span class="sxs-lookup"><span data-stu-id="3dba2-106">Expected Values</span></span>      |
|-------------------------------|--------------------------|
|                               | <span data-ttu-id="3dba2-107">BTAD_ChangeRequestAction</span><span class="sxs-lookup"><span data-stu-id="3dba2-107">BTAD_ChangeRequestAction</span></span> |
| <span data-ttu-id="3dba2-108">不使用覆寫旗標匯入</span><span class="sxs-lookup"><span data-stu-id="3dba2-108">Import without overwrite flag</span></span> |          <span data-ttu-id="3dba2-109">建立</span><span class="sxs-lookup"><span data-stu-id="3dba2-109">Create</span></span>          |
|  <span data-ttu-id="3dba2-110">使用覆寫旗標匯入</span><span class="sxs-lookup"><span data-stu-id="3dba2-110">Import with overwrite flag</span></span>   |          <span data-ttu-id="3dba2-111">Update</span><span class="sxs-lookup"><span data-stu-id="3dba2-111">Update</span></span>          |
|            <span data-ttu-id="3dba2-112">安裝</span><span class="sxs-lookup"><span data-stu-id="3dba2-112">Install</span></span>            |          <span data-ttu-id="3dba2-113">Update</span><span class="sxs-lookup"><span data-stu-id="3dba2-113">Update</span></span>          |
|           <span data-ttu-id="3dba2-114">Uninstall</span><span class="sxs-lookup"><span data-stu-id="3dba2-114">Uninstall</span></span>           |          <span data-ttu-id="3dba2-115">DELETE</span><span class="sxs-lookup"><span data-stu-id="3dba2-115">Delete</span></span>          |
|        <span data-ttu-id="3dba2-116">匯入回復</span><span class="sxs-lookup"><span data-stu-id="3dba2-116">Import rollback</span></span>        |          <span data-ttu-id="3dba2-117">DELETE</span><span class="sxs-lookup"><span data-stu-id="3dba2-117">Delete</span></span>          |
|       <span data-ttu-id="3dba2-118">安裝回復</span><span class="sxs-lookup"><span data-stu-id="3dba2-118">Install rollback</span></span>        |          <span data-ttu-id="3dba2-119">DELETE</span><span class="sxs-lookup"><span data-stu-id="3dba2-119">Delete</span></span>          |

## <a name="see-also"></a><span data-ttu-id="3dba2-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3dba2-120">See Also</span></span>  
 <span data-ttu-id="3dba2-121">[使用前置和後置處理指令碼自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md) </span><span class="sxs-lookup"><span data-stu-id="3dba2-121">[Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md) </span></span>  
 <span data-ttu-id="3dba2-122">[BTAD_ChangeRequestAction](../core/btad-changerequestaction.md) </span><span class="sxs-lookup"><span data-stu-id="3dba2-122">[BTAD_ChangeRequestAction](../core/btad-changerequestaction.md) </span></span>  
 <span data-ttu-id="3dba2-123">[BTAD_InstallMode](../core/btad-installmode.md) </span><span class="sxs-lookup"><span data-stu-id="3dba2-123">[BTAD_InstallMode](../core/btad-installmode.md) </span></span>  
 [<span data-ttu-id="3dba2-124">BTAD_HostClass</span><span class="sxs-lookup"><span data-stu-id="3dba2-124">BTAD_HostClass</span></span>](../core/btad-hostclass.md)