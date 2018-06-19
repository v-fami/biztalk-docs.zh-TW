---
title: BTAD_InstallMode |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BTAD_InstallMode [environment variable]
ms.assetid: b0ca48b8-c672-4704-9a04-2c6f159e57be
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2bcb527bda0a8ee2bfb36b06d317d952b48e699
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231110"
---
# <a name="btadinstallmode"></a><span data-ttu-id="c77d7-102">BTAD_InstallMode</span><span class="sxs-lookup"><span data-stu-id="c77d7-102">BTAD_InstallMode</span></span>
<span data-ttu-id="c77d7-103">BTAD_InstallMode 會描述 BizTalk 應用程式部署的安裝模式。</span><span class="sxs-lookup"><span data-stu-id="c77d7-103">BTAD_InstallMode describes the installation mode for BizTalk application deployment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c77d7-104">備註</span><span class="sxs-lookup"><span data-stu-id="c77d7-104">Remarks</span></span>  
 <span data-ttu-id="c77d7-105">下表描述 BTAD_InstallMode 的可能值。</span><span class="sxs-lookup"><span data-stu-id="c77d7-105">The following table describes the possible values for BTAD_InstallMode.</span></span>  
  
|<span data-ttu-id="c77d7-106">Value</span><span class="sxs-lookup"><span data-stu-id="c77d7-106">Value</span></span>|<span data-ttu-id="c77d7-107">說明</span><span class="sxs-lookup"><span data-stu-id="c77d7-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c77d7-108">Install</span><span class="sxs-lookup"><span data-stu-id="c77d7-108">Install</span></span>|<span data-ttu-id="c77d7-109">建立或更新 BizTalkHostInstance (本機電腦)</span><span class="sxs-lookup"><span data-stu-id="c77d7-109">Create or update to BizTalkHostInstance (the local computer)</span></span>|  
|<span data-ttu-id="c77d7-110">匯入</span><span class="sxs-lookup"><span data-stu-id="c77d7-110">Import</span></span>|<span data-ttu-id="c77d7-111">建立或更新 ConfigurationDb (群組的 BizTalk 管理資料庫)</span><span class="sxs-lookup"><span data-stu-id="c77d7-111">Create or update to ConfigurationDb (the BizTalk Management database for the group)</span></span>|  
|<span data-ttu-id="c77d7-112">Uninstall</span><span class="sxs-lookup"><span data-stu-id="c77d7-112">Uninstall</span></span>|<span data-ttu-id="c77d7-113">從 BizTalkHostInstance (本機電腦) 刪除</span><span class="sxs-lookup"><span data-stu-id="c77d7-113">Delete from BizTalkHostInstance (the local computer)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c77d7-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c77d7-114">See Also</span></span>  
 <span data-ttu-id="c77d7-115">[前置和後置處理指令碼環境變數](../core/pre-and-post-processing-script-environment-variables.md) </span><span class="sxs-lookup"><span data-stu-id="c77d7-115">[Pre- and Post-processing Script Environment Variables](../core/pre-and-post-processing-script-environment-variables.md) </span></span>  
 [<span data-ttu-id="c77d7-116">環境變數如何指示部署狀態</span><span class="sxs-lookup"><span data-stu-id="c77d7-116">How Environment Variables Indicate Deployment State</span></span>](../core/how-environment-variables-indicate-deployment-state.md)