---
title: 錯誤-運算質有任何輸入 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.functiodHasNoInput
ms.assetid: ea59b902-953d-4a5f-aa28-dbaa0a017dca
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fd2626d0b3332ddbf2def47502e7b323a0ae0e7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000775"
---
# <a name="error---functoid-has-no-input"></a>錯誤-運算質有沒有輸入
**錯誤碼**  

 btm1012  

 **說明**  

 指定的運算質至少需要一個輸入參數，卻沒有指定輸入參數。  

 **使用者動作**  

 使用下列一或兩種方式，針對指定的運算質提供適當數目的輸入參數，應特別注意輸入參數的順序：  

- 使用拖曳方式在指定的運算質與來源結構描述中之節點或其他運算質之輸出間建立連結，這些節點位於指定運算質左邊的地圖格線頁中。  

- 選取指定的運算質，然後按一下省略符號 (**...**) 按鈕相關聯**輸入參數**屬性，在 Microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗中，然後設定並重新安排輸入參數順序**設定\<運算質\>運算質** 對話方塊。 您可以在此對話方塊中建立常數輸入參數、賦予這些參數值，並使用相對於其他輸入參數的順序排列這些參數。
