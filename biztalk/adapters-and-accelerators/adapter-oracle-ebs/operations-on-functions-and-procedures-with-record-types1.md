---
title: 函數和程序的記錄 Types1 上的作業 |Microsoft 文件
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
ms.openlocfilehash: 43974d1c392a357b9781ff7f6fae5286e282513a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216078"
---
# <a name="operations-on-functions-and-procedures-with-record-types"></a>函數和程序的記錄類型的作業
Oracle 記錄類型可用來代表階層式參數傳遞至 PL/SQL 函數和程序中的資訊。 [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現記錄類型為複雜的 XML 型別。 

## <a name="supported-record-types"></a>支援的記錄類型
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]支援下列幾種記錄類型：  
  
-   記錄會宣告為預存程序和函式中的資料表 %資料列型別參數的類型。  
  
-   宣告類型的記錄中當做參數的 PL/SQL 封裝的記錄類型。 例如，輸入 rec_type1 是 RECORD(name varchar2(100), age number(3));  
  
-   包含巢狀的記錄的記錄類型。  
  
-   記錄中出現的類型為，逾時或在 OUT 參數的程序或函式。  
  
-   傳回值的函式的記錄類型。  
  
    > [!NOTE]
    >  [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援 BFILE 做為記錄成員的類型。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)