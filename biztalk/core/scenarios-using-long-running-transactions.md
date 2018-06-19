---
title: 使用長時間執行交易的案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transactions, long-running
- long-running transactions, timeouts
- transactions, examples
- long-running transactions, examples
- long-running compensations
- examples, long-running transactions
- examples, custom compensations
ms.assetid: 76b3e0f8-44dc-419e-a73a-c2908b1d8795
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05ac14bc6e333f963dda7cb9b33d1ebf371c0546
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269918"
---
# <a name="scenarios-using-long-running-transactions"></a>使用長時間執行交易的案例
下列案例說明長時間執行交易的用途。  
  
## <a name="scenario-1-using-long-running-transactions-with-timeouts"></a>案例 1： 使用長時間執行交易的逾時  
 長時間執行範圍可以和逾時相關聯，這是長時間執行工作必須完成的邏輯時間。 如果指定的時間，預先定義的系統例外狀況內沒有完成範圍**TimeoutException** ，就會引發。  
  
 您可以將整個協調流程標示為長時間執行，或在外部長時間執行範圍中巢狀處理任何其他範圍，來建立長時間執行程序。 在前面的案例中，系統提供的例外狀況處理常式會執行，而在後面的案例中，則允許將特定例外狀況處理常式與外部範圍產生關聯。 系統提供的預設例外狀況處理常式會針對每個順利完成的巢狀交易式範圍 (如果有的話)，以其完成的相反順序，執行補償處理常式。 您可以在長時間執行交易的例外狀況處理常式中使用 [補償] 圖形，透過自我補償達到相同結果。  
  
 下列協調流程說明如何將逾時與長時間執行交易產生關聯。  
  
 **使用逾時的長時間執行交易**  
  
 ![長時間執行交易的逾時與](../core/media/bts-trans-orch-fig7.gif "BTS_Trans_Orch_Fig7")  
  
 有時候您可能需要與透過批次方式運作的舊有系統互動。 這個案例顯示舊有系統收發訂單。 舊有系統會處理訂單並傳回訂單通知。 傳送作業會使用訂單編號初始化相互關聯集，並且在該相互關聯集之後發生接收作業。 接收作業也位在具有逾時值的長時間執行範圍內。  
  
 協調流程引擎會凍結等待接收的協調流程執行個體。 相互關聯會確保在接收訊息之後叫用相同的協調流程執行個體。 如果訂單通知未在逾時值，所指定的時間間隔內到達**TimeoutException**就會擲回。  
  
## <a name="scenario-2-using-long-running-transactions-with-custom-compensation"></a>案例 2： 使用長時間執行交易搭配自訂補償  
 下列協調流程示範如何將自訂補償與整個協調流程產生關聯並叫用關聯的自訂補償。 這個案例會插入新客戶，並插入該客戶的訂單詳細資料。 此協調流程的邏輯指出，如果訂單插入失敗，您應該回復客戶插入。 客戶插入無法做到舊有系統，因此，個別呼叫的協調流程中所示範。 呼叫的協調流程**自訂**屬性集，以便提供個別的工作表，來執行補償程序的補償。 補償將會刪除新插入的客戶。  
  
 呼叫端協調流程具有長時間執行範圍以執行訂單插入。 這個範圍是以巢狀方式放在外部長時間執行範圍內。 外部範圍關聯的例外狀況處理常式會攔截任何例外狀況。 此處理常式會使用 [補償] 圖形，叫用與被呼叫端協調流程關聯的自訂例外狀況，以回復對協調流程的呼叫中可能發生的任何變更。  
  
 **自訂補償使用長時間執行交易**  
  
 ![長時間執行交易搭配自訂補償](../core/media/bts-trans-orch-fig8.gif "BTS_Trans_Orch_Fig8")  
  
 **呼叫端協調流程 （主要）**  
  
 ![呼叫協調流程 &#40; 主要 &#41;] (../core/media/bts-trans-orch-fig9.gif "BTS_Trans_Orch_Fig9")  
  
 **呼叫端協調流程 （補償）**  
  
 ![呼叫協調流程 &#40; 補償 &#41;] (../core/media/bts-trans-orch-fig10.gif "BTS_Trans_Orch_Fig10")