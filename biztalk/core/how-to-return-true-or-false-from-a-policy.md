---
title: 如何從原則傳回 True 或 False |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a7bb9b2-14aa-44e7-a290-e49bf53bc594
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 281d5ab7648545f2e0616095f3c535d7d109136f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254406"
---
# <a name="how-to-return-true-or-false-from-a-policy"></a>如何從原則傳回 True 或 False
您不能為原則直接指定傳回類型。 不過，您可以將下列其中一個事實類型傳送給原則，讓原則將事實的值變更為 `true` 或 `false`，然後在執行原則後檢查屬性/項目/欄的值：  
  
-   具有 `Boolean` 類型之屬性的 .NET 物件  
  
-   具有 `Boolean` 類型之項目的 XML 文件  
  
-   具有 `Boolean` 類型之欄的資料庫資料表