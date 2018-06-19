---
title: 錯誤-升級的屬性 Max Occurs |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.promoPropMaxOccurs
ms.assetid: fc07367e-40f2-46e9-aeeb-bfa2498b1b37
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9c8395757d19eff5241d47c31b15409a00b6faf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239862"
---
# <a name="error---promoted-property-max-occurs"></a>錯誤-升級的屬性 Max Occurs
**錯誤碼**  
  
 BEC2002  
  
 **說明**  
  
 設定**Max Occurs**其中一個上階節點，或正在升級之節點的屬性是與屬性升級不相容。 在執行個體訊息中可以發生一次以上的節點，不允許屬性升級。 因此， **Max Occurs**從正在升級回根節點之節點的所有節點的屬性必須設定為 1。  
  
 **使用者動作**  
  
 請確認**Max Occurs**正在升級之節點和它的所有上階節點的屬性設定為一 (1)。