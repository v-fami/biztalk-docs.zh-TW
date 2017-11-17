---
title: "管理 BAM 定義檔案所需的使用者權限 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb4fb73f-b783-4a04-9bd6-a135b3dd2655
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d5e39c86eec0cf198a5b879cbc98d29321de71dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="required-user-rights-for-managing-bam-definition-files"></a><span data-ttu-id="a0f21-102">管理 BAM 定義檔案所需的使用者權限</span><span class="sxs-lookup"><span data-stu-id="a0f21-102">Required User Rights for Managing BAM Definition Files</span></span>
<span data-ttu-id="a0f21-103">任何角色中的使用者都可以建立、管理和檢視 BAM 定義檔案。</span><span class="sxs-lookup"><span data-stu-id="a0f21-103">BAM definition files can be created, managed, and viewed by users in any role.</span></span> <span data-ttu-id="a0f21-104">管理 BAM 定義檔案包括了部署和移除定義檔案，以及管理與定義檔案關聯的活動、檢視、警示和成品。</span><span class="sxs-lookup"><span data-stu-id="a0f21-104">Managing BAM definition files includes deploying and removing them as well as managing the activities, views, alerts, and artifacts that are associated with the definition file.</span></span>  
  
 <span data-ttu-id="a0f21-105">系統管理員必須維護適當的資產保護，例如使用適當的存取權限建立共用資料夾。</span><span class="sxs-lookup"><span data-stu-id="a0f21-105">Administrators should maintain proper asset protection, such as creating shared folders with appropriate access permissions.</span></span> <span data-ttu-id="a0f21-106">使用 Excel 的 BAM 增益集時，我們建議使用者將巨集安全性層級設定為高。</span><span class="sxs-lookup"><span data-stu-id="a0f21-106">When using the BAM Add-In for Excel, we recommend that users set the macro security level to high.</span></span>  
  
 <span data-ttu-id="a0f21-107">修改 BAM 定義檔不需要任何必要的使用者權限 (視存放定義檔案位置所設定的權限而定)。</span><span class="sxs-lookup"><span data-stu-id="a0f21-107">There are no required user rights needed to modify the BAM definition files (depending on permissions set on where the definition files are stored).</span></span> <span data-ttu-id="a0f21-108">對定義檔案所做的變更不會自動套用至 BAM 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="a0f21-108">Changes to definition files are not automatically applied to the BAM infrastructure.</span></span> <span data-ttu-id="a0f21-109">若要套用變更，您必須使用 BAM 管理公用程式。</span><span class="sxs-lookup"><span data-stu-id="a0f21-109">To apply the changes you must use the BAM Management utility.</span></span>  
  
 <span data-ttu-id="a0f21-110">若要使用 BAM 管理公用程式，您必須是要套用 BAM 定義之電腦的系統管理員，或是 BizTalk Server 系統管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="a0f21-110">To use the BAM Management utility, you must be an administrator on the computer to which the BAM definition is being applied or a member of the BizTalk Server Administrators group.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0f21-111">在支援 [使用者帳戶控制] (UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="a0f21-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0f21-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0f21-112">See Also</span></span>  
 <span data-ttu-id="a0f21-113">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="a0f21-113">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="a0f21-114">[何謂 BAM 定義？](../core/what-is-a-bam-definition.md) </span><span class="sxs-lookup"><span data-stu-id="a0f21-114">[What Is a BAM Definition?](../core/what-is-a-bam-definition.md) </span></span>  
 [<span data-ttu-id="a0f21-115">如何部署 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="a0f21-115">How to Deploy BAM Definitions</span></span>](../core/how-to-deploy-bam-definitions.md)