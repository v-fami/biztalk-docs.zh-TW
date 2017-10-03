---
title: "函式和預存的 Procedures1 上的作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e6bdaa7-ed3c-43bc-bed5-70fe43f9c2d1
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfe5f705c8e432c920c8fae41a2b2f050c188047
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-functions-and-stored-procedures"></a>函式和預存程序的作業
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]支援 Oracle 函式和程序。

## <a name="functions-and-procedures"></a>函數和程序

[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]支援 Oracle 函數和程序如下：  
  
-   **函式**當成作業。 作業名稱是 Oracle 函式的名稱。 在 OUT、 出參數都有支援，以及，傳回值。  
  
    > [!IMPORTANT]
    >  如果您的函式中傳遞了無效的參數 （也就是傳遞的數值欄位的字串值），[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可能會擲回例外狀況根據 ODP.NET 的行為。 這是因為[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用 ODP.NET Oracle E-business Suite 與通訊。  
  
-   **程序**當成作業。 作業名稱是 Oracle 程序的名稱。 OUT、] 和 [出支援參數。  
  
    > [!IMPORTANT]
    >  在程序，如果您插入或更新的介面資料表或資料庫資料表中數值欄位的十進位值 (例如，15.2)[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]將會擲回例外狀況。 這是因為[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用利用 Oracle E-business Suite，通訊 ODP.NET 和 ODP.NET 不支援接受的數值欄位的十進位值。  
  
-   **REF CURSOR 類型**支援 IN 和 OUT 參數的程序和函式，以及函式傳回值。 如需詳細資訊，請參閱[函式和有 REF CURSOR 參數的程序上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-ref-cursor-parameters1.md)。  
  
-   **記錄類型**IN、 支援，而在 OUT 參數的程序和函式，以及函式傳回值。 支援簡單和複雜 （巢狀） 的記錄類型。 [函數和程序的記錄類型的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-record-types1.md)  
  
> [!NOTE]
>  您也可以設定函式和預存程序中的應用程式內容[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 應用程式內容，以及如何設定它的相關資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)