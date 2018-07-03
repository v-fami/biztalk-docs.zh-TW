---
title: Oracle 資料庫中執行複合作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b877d8e3-2016-40e8-888f-6b768021d6b8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd5bc7e1454cb00b3f163ec7201de327fccbd637
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001439"
---
# <a name="run-composite-operations-in-oracle-database"></a>Oracle 資料庫中執行複合作業
[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓配接器用戶端執行複合作業可包含任意數目的下列作業，並依照任何順序：  
  
- 選取、 插入、 更新和刪除資料表和檢視上的作業。  
  
- 預存程序、 函數和程序或當成作業配接器中的封裝內的函式。  
  
  資料表和檢視表相同的資料庫或不同的資料庫中的複合運算中的作業可以為目標。 不過，資料無法共用，或在複合作業中的不同作業間重複使用。 比方說，在複合作業中，選取作業的結果集不能用於做為輸入參數的預存程序。  
  
  複合作業中的每項作業會使用個別的連接。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]取用 ODP.NET 連接集區的連線數目上限為在複合作業中，作業數目及取得執行的作業，然後再釋放連接。 不過，複合作業的作業會傳回結果集，如果連接已釋放，才使用訊息。  
  
> [!IMPORTANT]
>  如果您執行複合作業時遇到逾時問題則可能是因為連線的數目小於中複合作業牽涉到的作業數目：  
> 
> - 做為 OUT 包含 BFILE、 BLOB、 CLOB、 NCLOB、 和 REF CURSOR 的預存程序或在 OUT 參數。  
>   -   選取作業。  
> 
>   若要解決此問題，您必須確定有"n"這類的複合運算中的作業數目，為指定的值**MinPoolSize**繫結屬性是"n + 1"或更新版本。 如需詳細資訊**MinPoolSize**繫結屬性，請參閱[Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
 如需詳細資訊：  
  
- 如何執行中的複合作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[Oracle 資料庫所使用的 BizTalk Server 上執行複合操作](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md)。  
  
- 訊息複合作業的結構描述，請參閱[複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)