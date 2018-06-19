---
title: 警告-找不到辨別的欄位 XPath |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.distingFieldXPathNotFound
ms.assetid: a925c39c-9ae1-4334-b329-aa2f5afd97ce
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9df2e34c27fe3e5e3540ac384443f86143bf741
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288158"
---
# <a name="warning---distinguished-field-xpath-not-found"></a><span data-ttu-id="7f6a0-102">警告-找不到辨別的欄位 XPath</span><span class="sxs-lookup"><span data-stu-id="7f6a0-102">Warning - Distinguished Field XPath Not Found</span></span>
<span data-ttu-id="7f6a0-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="7f6a0-103">**Error Code**</span></span>  
  
 <span data-ttu-id="7f6a0-104">BEC1006</span><span class="sxs-lookup"><span data-stu-id="7f6a0-104">BEC1006</span></span>  
  
 <span data-ttu-id="7f6a0-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="7f6a0-105">**Explanation**</span></span>  
  
 <span data-ttu-id="7f6a0-106">對應至指定「辨別欄位」屬性之節點可能不存在於結構描述中。</span><span class="sxs-lookup"><span data-stu-id="7f6a0-106">The node corresponding to the indicated Distinguished Field promotion may not exist in the schema.</span></span> <span data-ttu-id="7f6a0-107">BizTalk 編輯器無法解析複雜 XPath 規格，而且如果您編輯升級的屬性 XPath 中**編輯執行個體 XPath**對話方塊中，可能或可能無法正確識別您要升級的節點。</span><span class="sxs-lookup"><span data-stu-id="7f6a0-107">BizTalk Editor cannot resolve complex XPath specifications, and if you edited the promoted property XPath in the **Edit Instance XPath** dialog box, it may or may not correctly identify the node you intended to promote.</span></span>  
  
 <span data-ttu-id="7f6a0-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="7f6a0-108">**User Action**</span></span>  
  
 <span data-ttu-id="7f6a0-109">您可以避免此警告訊息出現藉由變更升級屬性的 XPath**編輯執行個體 XPath**對話方塊中，您可以從中的資料格存取**節點路徑**上資料表的資料行**辨別欄位**索引標籤中**升級屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7f6a0-109">You can keep this warning from appearing by changing the XPath for the promoted property in the **Edit Instance XPath** dialog box, which you can access from cells in the **Node Path** column of the table on the **Distinguished Fields** tab in the **Promote Properties** dialog box.</span></span> <span data-ttu-id="7f6a0-110">您可以存取**升級屬性**對話方塊從**升級屬性**屬性**結構描述**Microsoft® 節點[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗。</span><span class="sxs-lookup"><span data-stu-id="7f6a0-110">You can access the **Promote Properties** dialog box from the **Promote Properties** property of the **Schema** node in the Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.</span></span>