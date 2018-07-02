---
title: 支援 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: afdd1a5b-2a6b-48b8-a659-afd81f43f34b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 592c61fd821920656cc12744f290505828cadcd9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981367"
---
# <a name="support-for-executenonquery-executereader-and-executescalar-operations"></a>支援 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]會公開下列的輸出作業的根層級：  
  
-   **ExecuteNonQuery**： 使用任何任意的 SQL 陳述式或 PL/SQL 區塊執行 Oracle E-business Suite 中，如果您想要傳回多個結果集的這項作業。 此函式的輸入的參數包含字串參數 （整個 PL/SQL 區塊執行） 和字串 (OutRefCursorNames) 陣列。 OutRefCursorNames 中指定每個字串值會假設為與具有相同名稱傳回 REF CURSOR 的 PL/SQL 區塊的 REF CURSOR 輸出參數名稱。 此函式也會為 OUT 參數 (OutRefCursors)，也就是資料集的陣列。 資料集的相關資訊，請參閱 Oracle 文件[ http://go.microsoft.com/fwlink/?LinkId=124538 ](http://go.microsoft.com/fwlink/?LinkId=124538)。 這項作業的傳回值是整數資料類型，並指出受影響的資料列數。  
  
-   **ExecuteReader**： 任何任意的 SQL 陳述式或 PL/SQL 區塊執行 Oracle E-business Suite 中，如果您想要的結果集傳回的資料集使用此作業。 此作業會接受字串參數做為輸入，並傳回資料集。  
  
-   **ExecuteScalar**： 使用此操作將任何任意的 SQL 陳述式或 PL/SQL 區塊執行 Oracle E-business Suite 中，如果您想要傳回的只有一個值。 如果結果集傳回的值，只有第一個資料列的第一個資料行中的值會傳回 XML 字串格式。  
  
> [!NOTE]
> - ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業不支援使用者定義型別 (Udt)。  
>   - 您也可以設定中的 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的應用程式內容[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 它是必要設定的 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的應用程式內容，如果任一項作業的目標 （介面資料表、 介面檢視、 同時執行的程式或要求，Oracle E-business Suite 中的成品設定）。 應用程式內容，以及如何將它設定的相關資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)