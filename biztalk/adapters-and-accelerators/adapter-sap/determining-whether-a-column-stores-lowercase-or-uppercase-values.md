---
title: "判斷資料行是否儲存大寫或小寫值 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1edc8332-d8c7-4040-895b-f121fb03df44
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93b54c00b43192462fb095dbfbfda4cbf0b248a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="determining-whether-a-column-stores-lowercase-or-uppercase-values"></a>決定是否以值的資料行存放區大寫或小寫
此區段會列出要對 SAP 系統以判定是否 SAP 資料表的資料行儲存大寫或小寫字元的高階工作。 如需詳細指示如何執行這項工作中，您必須連絡您的 SAP 系統管理員，或請參閱 SAP 文件。  
  
### <a name="to-determine-the-case-of-values-stored-in-a-column"></a>若要判斷值儲存在資料行的大小寫  
  
1.  啟動 SAP GUI。  
  
2.  移至交易 SE37，並執行 DDIF_TABL_GET。  
  
3.  NAME 參數，指定包含您要判斷字元大小寫資訊的資料行的資料表名稱。 例如，KNA1。  
  
4.  第一個資料表參數是 DD03P_TAB。 按一下以查看資料表中的資料列的參數。 此資料表中的每個資料列對應到資料行 （例如 KNA1) 資料表中指定步驟 3 中。  
  
5.  在 DD03P_TAB，尋找小寫的資料行，每個資料列中的值。 如果小寫的資料行中的值是 'X'，對應的資料行中的資料表 （例如 KNA1)，可將小寫和大寫字元。 小寫的資料行中的值是空的如果對應的資料行只能儲存大寫字元。  
  
     例如，名稱資料列的大小寫的資料行是 X。因此，KNA1 的 NAME 資料行可儲存大寫和小寫字元。 不過，LAND1 列小寫的資料行是空的。 因此，LAND1 資料表中的資料行 KNA1 只能儲存大寫字元。  
  
## <a name="see-also"></a>另請參閱  
 [使用特定 SAP 配接器實例的 SAP GUI 執行工作](../../adapters-and-accelerators/adapter-sap/performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)