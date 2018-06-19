---
title: 如何在協調流程上設定交易屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- atomic transactions
- orchestrations, transactions
- transactions, long-running
- orchestrations, configuring
- transactions, atomic
ms.assetid: 8eec6019-4d96-4ed6-8a90-9403738d8af4
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9164a9f5670a996a62450a19d802c97b89d8e242
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248814"
---
# <a name="how-to-configure-transactional-properties-on-an-orchestration"></a>如何在協調流程上設定交易屬性
協調流程可視為不可部分完成的交易、長時間執行的交易，或兩者皆非。  
  
### <a name="to-make-your-orchestration-an-atomic-transaction"></a>讓協調流程變成不可部分完成的交易  
  
1.  在 [協調流程檢視] 視窗中，選取**協調流程屬性**。  
  
2.  在 [屬性] 視窗中，選取**不可部分完成**的下拉式清單中**交易類型**屬性。  
  
     **批次**，**補償**，**隔離等級**，**重試**，**逾時**，和**交易識別項**就如同任何範圍，會顯示為 [屬性] 視窗中的屬性。 如需有關這些屬性的詳細資訊，請參閱[如何設定 「 範圍 」 圖形](../core/how-to-configure-the-scope-shape.md)。  
  
### <a name="to-make-your-orchestration-a-long-running-transaction"></a>讓協調流程變成長時間執行的交易  
  
1.  在 [協調流程檢視] 視窗中，選取**協調流程屬性**。  
  
2.  在 [屬性] 視窗中，選取**長時間執行**的下拉式清單中**交易類型**屬性。  
  
     **補償**，**逾時**，和**交易識別項**會顯示為 [屬性] 視窗中的屬性。 就像是任何範圍的屬性一樣。 如需有關這些屬性的詳細資訊，請參閱[如何設定 「 範圍 」 圖形](../core/how-to-configure-the-scope-shape.md)。  
  
## <a name="see-also"></a>另請參閱  
 [建立交易式協調流程](../core/making-orchestrations-transactional.md)