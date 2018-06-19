---
title: 重複使用和衍生類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 240145ea-be41-40ce-8edd-3d4d00e2baec
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2982fdf5e46f813669ff74b513615637aa699bd4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286614"
---
# <a name="type-reuse-and-derivations"></a>類型重複使用和衍生
在 XML 結構描述定義 (XSD) 語言中，複雜的全域類型所提供的機制，可用於定義能在您結構描述中不同位置重複使用、甚至重新定義的結構化資料類型。 最典型的範例或許是包括名稱、街道、城市、州等等的地址結構。 更進一步而言，名稱本身可能是包括姓氏、中間名和名字字串的結構。 若這個複雜結構是全域定義，則您可以在結構描述的多個位置中使用它，如送貨地址和帳單地址。  
  
 XSD 也提供從某個類型衍生另一個類型的機制。 這包括簡單內容類型和複雜內容類型。 例如，可以從簡單字串類型 (如 xs:string) 衍生出新的類型，如此新類型僅會允許少數特定字串做為合法值。 此類型的衍生在 XSD 中被視為由限制衍生，因為衍生類型所允許之值的限制會比基礎類型所允許的值還多。  
  
 涉及複雜類型的衍生範例可以在先前建議的地址型別中看到。 假設地址型別是指定為搭配特定國家/地區的地址，其中國家/地區本身已假設是在地址中。 若要延伸此種地址型別以處理國際地址，您可以從原始地址型別衍生出新的型別，然後將額外的資訊 (如國家/地區) 包括在衍生型別中。 此型別的衍生在 XSD 中被視為由擴充衍生，因為衍生型別擴充了基礎型別。  
  
 本節將描述型別重複使用，以及使用衍生重新定義重複使用型別的方式。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [複雜全域型別定義和命名](../core/complex-global-type-definition-and-naming.md)  
  
-   [使用複雜全域型別的方式](../core/ways-to-use-complex-global-types.md)  
  
-   [簡單型別衍生](../core/simple-type-derivation.md)