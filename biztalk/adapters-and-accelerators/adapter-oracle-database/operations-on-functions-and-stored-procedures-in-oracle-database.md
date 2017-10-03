---
title: "函式和 Oracle 資料庫中的預存程序上的作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- REF CURSOR
- packaged functions and procedures
- operations, on functions and stored procedures
- stored procedure
- RECORD type
- overloaded functions and procedures
ms.assetid: 18072b58-65b2-4da5-9433-ea0da4e2d4f4
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78181aae7921cad3996e4bd408e604857a2bd15e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-functions-and-stored-procedures-in-oracle-database"></a>函式和 Oracle 資料庫中的預存程序的作業
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]支援 Oracle 函數、 程序和封裝，以下列方式：  
  
-   **函式**當成作業。 作業名稱是 Oracle 函式的名稱。 在 OUT、 出參數都有支援，以及，傳回值。  
  
-   **程序**當成作業。 作業名稱是 Oracle 程序的名稱。 OUT、] 和 [出支援參數。  
  
-   **包裝函數和程序**當成作業。 Oracle 封裝的名稱限定的名稱和命名空間的作業 （函式或程序）。 多載支援 （請參閱下一個項目符號） 的封裝中。  
  
-   **多載函式和程序**在封裝中當成作業。 每個多載函式或程序會顯示與字串附加至其識別的多載的名稱。 此字串是組件的順序"overload1"、"overload2"、"overload3"，等等。  
  
-   **REF CURSOR 類型**IN、 支援，而在 OUT 參數的程序和函式，以及函式傳回值。 如需詳細資訊，請參閱[函式和有 REF CURSOR 參數的程序上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-ref-cursor-parameters1.md)。  
  
-   **記錄類型**IN、 支援，而在 OUT 參數的程序和函式，以及函式傳回值。 支援簡單和複雜 （巢狀） 的記錄類型。 [函數和程序的記錄類型的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-record-types1.md)  
  
 如需詳細資訊：  
  
-   透過使用叫用 Oracle 程序或函數[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[叫用函數及使用 BizTalk Server 的 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-biztalk-server.md)和[叫用多載函式和 Oracle 資料庫中的程序BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-overloaded-functions-and-procedures-in-oracle-database-using-biztalk-server.md)。  
  
-   叫用 Oracle 程序或函式使用 WCF 服務模型，請參閱[叫用函式和 Oracle 資料庫使用 WCF 服務模型中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)。  
  
-   叫用 Oracle 程序或函式使用 WCF 通道模型，請參閱[叫用使用 WCF 通道模型的 Oracle 資料庫中的函式](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md)。  
  
-   訊息結構和用來叫用 Oracle 程序和函式，請參閱的 SOAP 動作[函數和程序的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)