---
title: 函式和含有 RECORD 類型在 Oracle 資料庫中的程序作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RECORD type
ms.assetid: 28ecb76c-de82-43df-83cc-917c482417b3
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2635ac4b21173fe1a12603c60263dfa70b5a18e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974199"
---
# <a name="operations-on-functions-and-procedures-with-record-types-in-oracle-database"></a>函式和含有 RECORD 類型在 Oracle 資料庫中的程序作業
Oracle 記錄類型用來代表階層式參數傳遞至 PL/SQL 函數與程序中的資訊。 [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現複雜的 XML 類型的記錄類型。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援下列幾種記錄類型：  
  
- 記錄會宣告為預存程序和函式中的資料表 %資料列型別參數的類型。  
  
- 例如，宣告為類型的記錄參數的 PL/SQL 封裝中的記錄類型輸入 rec_type1 是 RECORD(name varchar2(100), age number(3));  
  
- 包含巢狀的記錄的記錄類型。  
  
- 記錄中出現的類型為，縮小或在 OUT 參數至程序或函式。  
  
- 是函式傳回值的記錄類型。  
  
  > [!NOTE]
  >  [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] Nepodporuje BFILE 做為記錄成員的類型。  
  
  如需詳細資訊：  
  
- 叫用函式或程序牽涉到使用 WCF 服務模型的記錄類型，請參閱[執行作業使用記錄類型在 Oracle 資料庫中使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md)。  
  
- 叫用函式或程序涉及記錄型別使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 叫用函式和程序的記錄類型，使用 BizTalk server](../../adapters-and-accelerators/adapter-oracle-database/run-functions-and-procedures-with-record-types-in-oracle-db-with-biztalk-server.md)。  
  
- 記錄的 XML 結構類型所支援之[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 記錄類型的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-record-types.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)