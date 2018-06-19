---
title: 訊息記錄類型的結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RECORD types, message schemas for
- RECORD types, support for
ms.assetid: 637c42f2-eed0-4941-a6cd-7e03d01088b8
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9022274041e06ad8ccc3f5243715d44d2b64282
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214134"
---
# <a name="message-schemas-for-record-types"></a>記錄類型的訊息結構描述
Oracle 記錄類型為結構化的 PL/SQL 資料類型所組成的一個或更簡單或結構化的資料庫類型。 記錄類型主要用於 PL/SQL 預存程序和函式中傳送和接收階層式資料。  
  
 [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]以下列方式支援記錄類型：  
  
-   記錄類型顯示為複雜型別。  
  
-   記錄類型可以是巢狀 （記錄在記錄中的）。  
  
-   記錄類型可以宣告為預存程序和函式中的資料表 %資料列型別參數。  
  
-   記錄類型可以宣告為 PL/SQL 封裝; 中的記錄型別參數例如， `TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));`。  
  
    > [!NOTE]
    >  [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援 BFILE 做為記錄成員的類型。  
  
 預存程序或函式中使用的記錄型別參數時，它是與該作業的命名空間限定的。 下列 XML 顯示在訊息中的記錄類型的結構：  
  
```  
<[REC_PARAM_NAME]>  
  <[FIELD_NAME1] xmlns="[OPERATION_NAMESPACE]">value1</[FIELD_NAME1]>  
  <[FIELD_NAME2] xmlns="[OPERATION_NAMESPACE]">value2</[FIELD_NAME2]>  
  …  
</[REC_PARAM_NAME]>  
```  
  
 [REC_PARAM_NAME] 是記錄參數的名稱。  
  
 [FIELD_NAME] 是中的記錄類型欄位的名稱。  
  
 [OPERATION_NAMESPACE] 是預存程序或函式在使用記錄參數的命名空間。  
  
 下列 XML 顯示巢狀的記錄類型欄位的記錄型別參數的結構：  
  
```  
<[REC_PARAM_NAME]>    
  <[FIELD_NAME1] xmlns="[OPERATION_NAMESPACE]">value1</[FIELD_NAME1]>  
  <[FIELD_NAME2] xmlns="[OPERATION_NAMESPACE]">value2</[FIELD_NAME2]>  
  <[REC_PARAM_NAME2]>  
    <[FIELD_NAME1] xmlns="[OPERATION_NAMESPACE]">value1</[FIELD_NAME1]>  
    <[FIELD_NAME2] xmlns="[OPERATION_NAMESPACE]">value1</[FIELD_NAME2]>  
    …  
  </[REC_PARAM_NAME2]>  
  …  
</[REC_PARAM_NAME]>  
```  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)