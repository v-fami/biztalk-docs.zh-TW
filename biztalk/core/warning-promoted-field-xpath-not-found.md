---
title: 警告-升級欄位 XPath 找不到 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.promoFieldXPathNotFound
ms.assetid: 21b8c240-5d6f-499d-8211-6e3f2ce2a79c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07f45bd1539817f010864226d07b76ca2feee8b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="warning---promoted-field-xpath-not-found"></a><span data-ttu-id="9e938-102">警告-升級欄位 XPath 找不到</span><span class="sxs-lookup"><span data-stu-id="9e938-102">Warning - Promoted Field XPath Not Found</span></span>
<span data-ttu-id="9e938-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="9e938-103">**Error Code**</span></span>  
  
 <span data-ttu-id="9e938-104">BEC1005</span><span class="sxs-lookup"><span data-stu-id="9e938-104">BEC1005</span></span>  
  
 <span data-ttu-id="9e938-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="9e938-105">**Explanation**</span></span>  
  
 <span data-ttu-id="9e938-106">對應至指定屬性欄位升級的節點可能不存在於結構描述中。</span><span class="sxs-lookup"><span data-stu-id="9e938-106">The node corresponding to the indicated property field promotion may not exist in the schema.</span></span> <span data-ttu-id="9e938-107">BizTalk 編輯器無法解析複雜 XPath 規格，而且如果您編輯升級的屬性 XPath 中**編輯執行個體 XPath**對話方塊中，可能或可能無法正確識別您要升級的節點。</span><span class="sxs-lookup"><span data-stu-id="9e938-107">BizTalk Editor cannot resolve complex XPath specifications, and if you edited the promoted property XPath in the **Edit Instance XPath** dialog box, it may or may not correctly identify the node you intended to promote.</span></span>  
  
 <span data-ttu-id="9e938-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="9e938-108">**User Action**</span></span>  
  
 <span data-ttu-id="9e938-109">您可以避免此警告訊息出現藉由變更升級屬性的 XPath**編輯執行個體 XPath**對話方塊中，您可以從中的資料格存取**節點路徑**資料行的**屬性欄位清單**資料表**屬性欄位**索引標籤中**升級屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9e938-109">You can keep this warning from appearing by changing the XPath for the promoted property in the **Edit Instance XPath** dialog box, which you can access from cells in the **Node Path** column of the **Property Field List** table on the **Property Fields** tab in the **Promote Properties** dialog box.</span></span> <span data-ttu-id="9e938-110">您可以存取**升級屬性**對話方塊從**升級屬性**屬性**結構描述**Microsoft® 節點[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗。</span><span class="sxs-lookup"><span data-stu-id="9e938-110">You can access the **Promote Properties** dialog box from the **Promote Properties** property of the **Schema** node in the Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.</span></span>