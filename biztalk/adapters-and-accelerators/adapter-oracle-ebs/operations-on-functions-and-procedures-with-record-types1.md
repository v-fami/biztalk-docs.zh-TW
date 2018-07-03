---
title: 函式和程序的記錄 Types1 作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: afc1c84f-2e36-493c-9ea8-4bc2248331db
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b7d4f392e863dd8966f5c011abfd6e602f2514c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006431"
---
# <a name="operations-on-functions-and-procedures-with-record-types"></a>函式和含有 RECORD 類型的程序作業
Oracle 記錄類型用來代表階層式參數傳遞至 PL/SQL 函數與程序中的資訊。 [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現複雜的 XML 類型的記錄類型。 

## <a name="supported-record-types"></a>支援的記錄類型
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]支援下列幾種記錄類型：  
  
- 記錄會宣告為預存程序和函式中的資料表 %資料列型別參數的類型。  
  
- 會宣告為類型的記錄參數的 PL/SQL 封裝中的記錄類型。 例如，輸入 rec_type1 是 RECORD(name varchar2(100), age number(3));  
  
- 包含巢狀的記錄的記錄類型。  
  
- 記錄中出現的類型為，縮小或在 OUT 參數至程序或函式。  
  
- 是函式傳回值的記錄類型。  
  
  > [!NOTE]
  >  [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] Nepodporuje BFILE 做為記錄成員的類型。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)