---
title: 轉換運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0cd7abcf-f524-4e85-b8d5-d6123767490f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 192db4b03f80674f2eb90be2255a8682454bde2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22237886"
---
# <a name="conversion-functoids"></a>轉換運算質

## <a name="overview"></a>概觀
**轉換**運算質可用數字和與其 ASCII 相等項，之間進行轉換，以將基底 10 個數字轉換成其基底 8 和基底 16 的對等項目。  
  
 所有轉換運算質都接受單一參數。  
  
> [!NOTE]
>  因為基礎類型系統中，變更**轉換**在這個版本的 BizTalk 對應工具運算質會產生比在舊版中產生稍微不同的結果。 例如，在舊版的 BizTalk 對應工具的輸入的值為-20 到**十六進位**運算質產生輸出結果為 0xFFEC。 在此版本中，當輸入值同樣為 -20，則產生的輸出為 0xFFFFFFEC。  

## <a name="available-functoids"></a>可用的運算質  
 **轉換**運算質為： 

* ASCII 到字元
* 字元到 ASCII
* 十六進位
* 八進位

這些運算質描述[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 

## <a name="see-also"></a>另請參閱  
 [如何新增基本運算質至對應](../core/how-to-add-basic-functoids-to-a-map.md)   
