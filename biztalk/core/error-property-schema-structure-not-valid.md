---
title: 錯誤-無效的屬性結構描述結構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.propSchemaStructNotValid<
ms.assetid: c5fd81a7-fa5a-4ec2-b895-00b280aca227
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b96634dc3a0b72b56f33107fc596d3bd29e40c7f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240310"
---
# <a name="error---property-schema-structure-not-valid"></a><span data-ttu-id="6abdc-102">錯誤-無效的屬性結構描述結構</span><span class="sxs-lookup"><span data-stu-id="6abdc-102">Error - Property Schema Structure Not Valid</span></span>
<span data-ttu-id="6abdc-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="6abdc-103">**Error Code**</span></span>  
  
 <span data-ttu-id="6abdc-104">BEC2007</span><span class="sxs-lookup"><span data-stu-id="6abdc-104">BEC2007</span></span>  
  
 <span data-ttu-id="6abdc-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="6abdc-105">**Explanation**</span></span>  
  
 <span data-ttu-id="6abdc-106">此屬性結構描述具有無效的結構。</span><span class="sxs-lookup"><span data-stu-id="6abdc-106">This property schema was found to have a structure that is not valid.</span></span> <span data-ttu-id="6abdc-107">屬性結構描述的是限制為一或多個**欄位項目**節點的子系**結構描述**節點。</span><span class="sxs-lookup"><span data-stu-id="6abdc-107">The structure of property schemas is limited to one or more **Field Element** nodes as children of the **Schema** node.</span></span>  
  
 <span data-ttu-id="6abdc-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="6abdc-108">**User Action**</span></span>  
  
 <span data-ttu-id="6abdc-109">更正這個屬性結構描述的結構，讓**結構描述**節點只包含**欄位項目**做為子系的節點。</span><span class="sxs-lookup"><span data-stu-id="6abdc-109">Correct the structure of this property schema so that the **Schema** node only has **Field Element** nodes as children.</span></span>