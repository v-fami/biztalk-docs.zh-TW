---
title: 選擇性節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- testing, BizTalk Mapper
- maps, testing
- testing, maps
- BizTalk Mapper, testing
- maps, optional nodes
ms.assetid: 7dcd203e-fb23-438a-87d1-42323acd87cc
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96cf7d8b22ee8469a7e52dba7bbad899209c5274
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263342"
---
# <a name="optional-nodes"></a>選擇性節點
使用選擇性節點將會在您測試對應時產生警告。 有兩種情況會將來源節點視為選擇性：  
  
-   實際的記錄或欄位為選擇性。  
  
-   必須要有來源記錄或欄位，但是父系、祖系和更高階層為選擇性。  
  
 可能的狀況是，來源結構描述中的記錄或欄位為選擇性，但是目的結構描述需要對應的記錄或欄位。  
  
 在這兩種可能的情況中，測試您的對應中產生警告**輸出**視窗。 此外，輸出資料將不包含目標節點。  
  
## <a name="see-also"></a>另請參閱  
 [測試對應](../core/testing-maps.md)