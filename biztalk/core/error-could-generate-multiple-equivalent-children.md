---
title: 錯誤-可能產生多個 Equivalent 子系 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.couldGenMultipleEquivChildren
ms.assetid: ef3ea6db-6759-4f38-804c-e32a1f24d758
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 686899c2871ded25f6901e919e9283694b9bacf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239766"
---
# <a name="error---could-generate-multiple-equivalent-children"></a><span data-ttu-id="11538-102">錯誤-可能產生多個 Equivalent 子系</span><span class="sxs-lookup"><span data-stu-id="11538-102">Error - Could Generate Multiple Equivalent Children</span></span>
<span data-ttu-id="11538-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="11538-103">**Error Code**</span></span>  
  
 <span data-ttu-id="11538-104">btm1026</span><span class="sxs-lookup"><span data-stu-id="11538-104">btm1026</span></span>  
  
 <span data-ttu-id="11538-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="11538-105">**Explanation**</span></span>  
  
 <span data-ttu-id="11538-106">目的結構描述的連結，不適當地啟用多個節點**相等**要產生的群組節點。</span><span class="sxs-lookup"><span data-stu-id="11538-106">Links to the destination schema inappropriately enable multiple nodes within an **Equivalent** group node to be generated.</span></span>  
  
 <span data-ttu-id="11538-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="11538-107">**User Action**</span></span>  
  
 <span data-ttu-id="11538-108">重新設定連結至目的結構描述，可能需要使用邏輯運算質，因此，只有單一節點內**相等**對應期間產生群組節點。</span><span class="sxs-lookup"><span data-stu-id="11538-108">Rework the links into the destination schema, potentially using logical functoids, so that only a single node within the **Equivalent** group node can be generated during mapping.</span></span>