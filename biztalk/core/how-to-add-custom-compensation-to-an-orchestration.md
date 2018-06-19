---
title: 如何新增自訂補償至協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, compensations
- Compensate shape [Orchestration Designer]
- Compensate shape [Orchestration Designer], orchestrations
- Compensation property
- orchestrations, transactional
- orchestrations, customizing
- customizing, orchestrations
- Compensate shape [Orchestration Designer], custom compensation
ms.assetid: d153498d-8f98-42ae-90b9-e3083d669aef
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3eadb9cba6e5a49be516a8095b01f93ca7a490f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248118"
---
# <a name="how-to-add-custom-compensation-to-an-orchestration"></a>如何新增自訂補償至協調流程
設定成長時間執行的協調流程交易可以包含用來回復或復原交易效果的自訂補償程式碼。 如果協調流程已順利完成，且已由另一個協調流程呼叫，呼叫的協調流程可以叫用其補償區塊使用**補償**圖形。  
  
### <a name="to-specify-that-an-orchestration-will-use-custom-compensation"></a>若要指定讓協調流程使用自訂補償  
  
1.  在 [協調流程檢視] 視窗中，選取**協調流程屬性**。  
  
2.  在 [屬性] 視窗中，選取**自訂**的下拉式清單中**補償**屬性。  
  
     **補償** 索引標籤旁會顯示**協調流程**在設計介面底部的索引標籤。  
  
### <a name="to-design-custom-compensation-for-an-orchestration"></a>若要設計協調流程的自訂補償  
  
1.  按一下**補償**在設計介面底部的索引標籤。  
  
     **補償設計介面**隨即出現。  
  
2.  新增圖形以**補償設計介面**方式與您在**協調流程設計介面**。  
  
     如需詳細資訊，請參閱[新增圖形至協調流程](../core/how-to-add-shapes-to-orchestrations.md)。  
  
## <a name="see-also"></a>另請參閱  
 [建立交易式協調流程](../core/making-orchestrations-transactional.md)