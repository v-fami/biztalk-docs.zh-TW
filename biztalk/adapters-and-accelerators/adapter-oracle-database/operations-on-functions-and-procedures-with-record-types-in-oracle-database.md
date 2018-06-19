---
title: 函式和 Oracle 資料庫中的記錄類型的程序上的作業 |Microsoft 文件
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
ms.openlocfilehash: 46daadeaa5d1fc1060217f044a9d143488c38d7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214406"
---
# <a name="operations-on-functions-and-procedures-with-record-types-in-oracle-database"></a>函數和程序與 Oracle 資料庫中的記錄類型的作業
Oracle 記錄類型可用來代表階層式參數傳遞至 PL/SQL 函數和程序中的資訊。 [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現記錄類型為複雜的 XML 型別。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援下列幾種記錄類型：  
  
-   記錄會宣告為預存程序和函式中的資料表 %資料列型別參數的類型。  
  
-   例如，宣告類型的記錄中當做參數的 PL/SQL 封裝的記錄類型輸入 rec_type1 是 RECORD(name varchar2(100), age number(3));  
  
-   包含巢狀的記錄的記錄類型。  
  
-   記錄中出現的類型為，逾時或在 OUT 參數的程序或函式。  
  
-   傳回值的函式的記錄類型。  
  
    > [!NOTE]
    >  [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援 BFILE 做為記錄成員的類型。  
  
 如需詳細資訊：  
  
-   叫用函式或程序牽涉到使用 WCF 服務模型的記錄類型，請參閱[執行作業使用記錄類型在 Oracle 資料庫中使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md)。  
  
-   叫用函式或程序涉及記錄類型使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[叫用函式和程序的記錄類型所使用的 BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-functions-and-procedures-with-record-types-in-oracle-db-with-biztalk-server.md)。  
  
-   記錄的 XML 結構類型支援的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[記錄類型的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-record-types.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)