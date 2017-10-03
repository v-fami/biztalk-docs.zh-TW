---
title: "訊息記錄類型的結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RECORD types, message schemas for
- RECORD types, support for
ms.assetid: 637c42f2-eed0-4941-a6cd-7e03d01088b8
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9022274041e06ad8ccc3f5243715d44d2b64282
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-record-types"></a><span data-ttu-id="6ee6a-102">記錄類型的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="6ee6a-102">Message Schemas for RECORD Types</span></span>
<span data-ttu-id="6ee6a-103">Oracle 記錄類型為結構化的 PL/SQL 資料類型所組成的一個或更簡單或結構化的資料庫類型。</span><span class="sxs-lookup"><span data-stu-id="6ee6a-103">Oracle RECORD types are structured PL/SQL data types that consist of one or more simple or structured database types.</span></span> <span data-ttu-id="6ee6a-104">記錄類型主要用於 PL/SQL 預存程序和函式中傳送和接收階層式資料。</span><span class="sxs-lookup"><span data-stu-id="6ee6a-104">RECORD types are primarily used in PL/SQL stored procedures and functions to send and receive hierarchical data.</span></span>  
  
 <span data-ttu-id="6ee6a-105">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]以下列方式支援記錄類型：</span><span class="sxs-lookup"><span data-stu-id="6ee6a-105">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] supports RECORD types in the following manner:</span></span>  
  
-   <span data-ttu-id="6ee6a-106">記錄類型顯示為複雜型別。</span><span class="sxs-lookup"><span data-stu-id="6ee6a-106">RECORD types are surfaced as complex types.</span></span>  
  
-   <span data-ttu-id="6ee6a-107">記錄類型可以是巢狀 （記錄在記錄中的）。</span><span class="sxs-lookup"><span data-stu-id="6ee6a-107">RECORD types can be nested (record in a record).</span></span>  
  
-   <span data-ttu-id="6ee6a-108">記錄類型可以宣告為預存程序和函式中的資料表 %資料列型別參數。</span><span class="sxs-lookup"><span data-stu-id="6ee6a-108">RECORD types can be declared as TABLE%ROWTYPE parameters in stored procedures and functions.</span></span>  
  
-   <span data-ttu-id="6ee6a-109">記錄類型可以宣告為 PL/SQL 封裝; 中的記錄型別參數例如， `TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));`。</span><span class="sxs-lookup"><span data-stu-id="6ee6a-109">RECORD types can be declared as TYPE of RECORD parameters in PL/SQL packages; for example, `TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6ee6a-110">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援 BFILE 做為記錄成員的類型。</span><span class="sxs-lookup"><span data-stu-id="6ee6a-110">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support BFILE types as RECORD members.</span></span>  
  
 <span data-ttu-id="6ee6a-111">預存程序或函式中使用的記錄型別參數時，它是與該作業的命名空間限定的。</span><span class="sxs-lookup"><span data-stu-id="6ee6a-111">When a RECORD type parameter is used in a stored procedure or a function, it is qualified with the namespace of that operation.</span></span> <span data-ttu-id="6ee6a-112">下列 XML 顯示在訊息中的記錄類型的結構：</span><span class="sxs-lookup"><span data-stu-id="6ee6a-112">The following XML shows the structure of a RECORD type in a message:</span></span>  
  
```  
<[REC_PARAM_NAME]>  
  <[FIELD_NAME1] xmlns="[OPERATION_NAMESPACE]">value1</[FIELD_NAME1]>  
  <[FIELD_NAME2] xmlns="[OPERATION_NAMESPACE]">value2</[FIELD_NAME2]>  
  …  
</[REC_PARAM_NAME]>  
```  
  
 <span data-ttu-id="6ee6a-113">[REC_PARAM_NAME] 是記錄參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="6ee6a-113">[REC_PARAM_NAME] is the name of the RECORD parameter.</span></span>  
  
 <span data-ttu-id="6ee6a-114">[FIELD_NAME] 是中的記錄類型欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="6ee6a-114">[FIELD_NAME] is the name of a field in the RECORD type.</span></span>  
  
 <span data-ttu-id="6ee6a-115">[OPERATION_NAMESPACE] 是預存程序或函式在使用記錄參數的命名空間。</span><span class="sxs-lookup"><span data-stu-id="6ee6a-115">[OPERATION_NAMESPACE] is the namespace of the stored procedure or function in which the RECORD parameter is being used.</span></span>  
  
 <span data-ttu-id="6ee6a-116">下列 XML 顯示巢狀的記錄類型欄位的記錄型別參數的結構：</span><span class="sxs-lookup"><span data-stu-id="6ee6a-116">The following XML shows the structure of a RECORD type parameter with a nested RECORD type field:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6ee6a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ee6a-117">See Also</span></span>  
 [<span data-ttu-id="6ee6a-118">訊息和訊息結構描述，BizTalk adapter for Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="6ee6a-118">Messages and Message Schemas for BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)