---
title: 函式和 Oracle 資料庫中的預存程序作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- REF CURSOR
- packaged functions and procedures
- operations, on functions and stored procedures
- stored procedure
- RECORD type
- overloaded functions and procedures
ms.assetid: 18072b58-65b2-4da5-9433-ea0da4e2d4f4
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 856e6bf882605737380f0bbe6185dce8a56c5828
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979607"
---
# <a name="operations-on-functions-and-stored-procedures-in-oracle-database"></a>函式和 Oracle 資料庫中的預存程序作業
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]支援 Oracle 函式、 程序，以及套件以下列方式：  
  
- **函式**當成作業。 作業的名稱是 Oracle 函式的名稱。 在外，和 OUT 參數都有支援，以及，傳回值。  
  
- **程序**當成作業。 作業的名稱是 Oracle 程序的名稱。 在外，和 OUT 參數支援。  
  
- **包裝函式和程序**當成作業。 Oracle 封裝的名稱被限定的名稱和命名空間的作業 （函式或程序）。 （請參閱下一步 的項目符號） 的套件支援多載。  
  
- **多載的函式和程序**在封裝中顯示為作業。 每個多載函式或程序的呈現與識別此多載其名稱後面附加的字串。 此字串是組件的順序 」 overload1"、"overload2 」、 「 overload3"，等等。  
  
- **REF CURSOR 類型**IN、 支援，而在 OUT 參數的程序和函式，以及函式的傳回值。 如需詳細資訊，請參閱 <<c0> [ 函式和含有 REF CURSOR 參數的程序作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-ref-cursor-parameters1.md)。  
  
- **記錄類型**IN、 支援，而在 OUT 參數的程序和函式，以及函式的傳回值。 支援簡單和複雜 （巢狀） 的記錄類型。 [函式和含有 RECORD 類型之程序的相關作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-record-types1.md)  
  
  如需詳細資訊：  
  
- 使用叫用 Oracle 程序或函式[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 叫用函式與使用 BizTalk Server 的 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-biztalk-server.md)和[叫用多載函式和 Oracle Database 中的程序BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-overloaded-functions-and-procedures-in-oracle-database-using-biztalk-server.md)。  
  
- 叫用 Oracle 程序或函式，使用 WCF 服務模型，請參閱[叫用函式和使用 WCF 服務模型的 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)。  
  
- 叫用 Oracle 程序或函式使用 WCF 通道模型，請參閱[叫用使用 WCF 通道模型的 Oracle 資料庫中的函式](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md)。  
  
- 訊息結構和 SOAP 動作，用來叫用 Oracle 程序和函數，請參閱 <<c0> [ 函式和程序的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)