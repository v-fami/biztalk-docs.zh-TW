---
title: 函式和預存的 Procedures1 作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1e6bdaa7-ed3c-43bc-bed5-70fe43f9c2d1
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3356b41fc7929c55794c65e804245ed231b19b18
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007823"
---
# <a name="operations-on-functions-and-stored-procedures"></a>函式和預存程序作業
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]支援 Oracle 函式和程序。

## <a name="functions-and-procedures"></a>函式和程序

[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]支援 Oracle 函式和程序，以下列方式：  
  
- **函式**當成作業。 作業的名稱是 Oracle 函式的名稱。 在外，和 OUT 參數都有支援，以及，傳回值。  
  
  > [!IMPORTANT]
  >  如果您的函式中傳遞了無效的參數 （也就是傳遞數值欄位的字串值），[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可能會擲回的例外狀況，取決於 ODP.NET 行為。 這是因為[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用 ODP.NET 與 Oracle E-business Suite 通訊。  
  
- **程序**當成作業。 作業的名稱是 Oracle 程序的名稱。 在外，和 OUT 參數支援。  
  
  > [!IMPORTANT]
  >  在程序，如果您插入或更新的介面資料表或資料庫資料表的數值欄位的十進位值 (例如，15.2)[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]將會擲回例外狀況。 這是因為[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與 Oracle E-business Suite，通訊 ODP.NET 和 ODP.NET 不支援十進位值的數值欄位的使用。  
  
- **REF CURSOR 類型**支援 IN 和 OUT 參數的程序和函式，以及函式的傳回值。 如需詳細資訊，請參閱 <<c0> [ 函式和含有 REF CURSOR 參數的程序作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-ref-cursor-parameters1.md)。  
  
- **記錄類型**IN、 支援，而在 OUT 參數的程序和函式，以及函式的傳回值。 支援簡單和複雜 （巢狀） 的記錄類型。 [函式和含有 RECORD 類型之程序的相關作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-record-types1.md)  
  
> [!NOTE]
>  您也可以設定函式和預存程序中的應用程式內容[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 如需應用程式內容，以及如何將它設定的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)