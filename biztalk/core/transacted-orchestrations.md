---
title: 交易式協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, compensations
- orchestrations, transactional
- Transaction Type property
ms.assetid: c4f0b6ca-d939-4d3a-b7ef-53c6aafdea9c
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8c6fb466e0c3cc5cae4a076237d1dbc970b5794
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278734"
---
# <a name="transacted-orchestrations"></a>交易的協調流程
協調流程可以是交易式流程，就像範圍一樣。 事實上，協調流程本身也可以視為範圍。 適用於交易協調流程的相同規則通常也適用於交易範圍。  
  
> [!NOTE]
>  協調流程和其他範圍之間的差異，在於協調流程沒有例外處理常式。  
  
## <a name="orchestration-compensation"></a>協調流程補償  
 如果**交易類型**協調流程屬性設定為長時間執行或不可部分完成，您也可以選取的值**補償**屬性，可以是預設或自訂。  
  
 如果您選取**自訂**補償，**補償** 索引標籤會出現在協調流程設計介面旁邊。 此索引標籤的外觀與協調流程設計介面相同，而且您也可以使用相同的方式在上面新增圖形和連接埠。  
  
 補償只會發生在其他協調流程所呼叫的協調流程上。 您可以使用補償特定的協調流程執行個體**識別碼**屬性**呼叫協調流程**圖形。  
  
> [!IMPORTANT]
>  如果補償存在最上層的協調流程，執行階段引擎將會忽略它。  
  
## <a name="see-also"></a>另請參閱  
 [建立交易式協調流程](../core/making-orchestrations-transactional.md)   
 [使用交易和例外狀況處理](../core/using-transactions-and-handling-exceptions.md)