---
title: 在 SAP 中 EXECQUERY 陳述式的語法 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 99bd7fbb-64f2-4327-a8ae-ccb574e56150
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ccf479438a5b0960a66b35ef7946df63d088284b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982015"
---
# <a name="syntax-for-an-execquery-statement-in-sap"></a>在 SAP 中 EXECQUERY 陳述式的語法
您可以使用 SAP GUI 來建立查詢，以圖形方式選取您想要查詢之資料行和排序的次序，您想要包含在結果集等資料表。[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]可讓使用者從 ADO.NET 應用程式中執行這類查詢，藉由提供使用者可用來執行 SAP 系統中定義的查詢 EXECQUERY 作業。  
  
 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]使用自訂的 RFC Z_EXECUTE_SAP_QUERY SAP 系統中執行的預先定義的查詢。 自訂 RFC 依次執行 RSAQ_REMOTE_QUERY_CALL，這是 SAP 系統中定義的 RFC 的標準。 因此，您可以使用 EXECQUERY 作業之前，您必須安裝自訂 RFC 的 SAP 系統，您將執行針對查詢中。 如需有關如何安裝自訂 RFC 的指示，請參閱 <<c0> [ 安裝適用於 SAP 的資料提供者的自訂 Rfc](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。  
  
 本主題提供 EXECQUERY 作業和其他有用的資訊與 EXECQUERY 作業相關的語法資訊。  
  
## <a name="syntax-for-an-execquery-statement"></a>EXECQUERY 陳述式的語法  
 下節描述的文法規格使用 EXECQUERY 作業[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。  
  
```  
EXECQUERY <QueryName> @USERGROUP='usergroup' [, @WORKSPACE='X'] [, @VARIANT='variant']   
[, @P1='<value 1>’] [, @P2='<value 2>'] ... [, @Pn = '<value n>'] [, @P1!='<value 3>'] [, @P1 > '<value 4>'] [, @P1 <= '<value 2>']   
[, NOT @P1 = '<value 2>'] [, NOT @P1 != '<value 2>'] [, NOT @P1 > '<value 2>']   
[, @P1 BETWEEN '<value 1>' AND '<value 2>'] [, NOT @P1 BETWEEN '<value 1>' AND '<value2>’]  
[OPTION 'USEORIGINALCOLUMNNAMES']  
  
```  
  
 其中：  
  
- **\<QueryName\>** 是 SAP 系統中定義的查詢名稱。  
  
- **USERGROUP**指的是在其中定義查詢的使用者群組。 這是強制參數。  
  
- **工作區**指的是在其中定義查詢的工作區。 在 SAP 中，有兩個工作區，標準和全域。 提供空白空間，以指定的標準工作區。 提供`X`指定通用的工作區。 預設值是空的空間。  
  
- **VARIANT**指的是一組儲存執行 SAP 查詢時，您可以指定的選取準則。 比方說，您可以使用變數來指定查詢的預設值。  
  
- <strong>@Pn</strong> n 是指<sup>th</sup> SAP 查詢定義中的選取項目欄位。  
  
- **USEORIGINALCOLUMNNAMES**指定提供者是否會使用原始的資料行名稱，在資料集中，因為它們存在於 SAP 系統。 根據預設，提供者會使用 SAP 查詢中所定義的易記名稱。 不過，如果在查詢中的易記名稱不是唯一的 ADO.NET 用戶端會擲回錯誤時讀取資料集的資料。 在此情況下，您必須指定 USEORIGINALCOLUMNNAMES 選項，表示提供者會在資料集中使用的原始資料行名稱。  
  
  > [!IMPORTANT]
  >  您必須永遠提供值選項關鍵字在單引號中，例如，'*USEORIGINALCOLUMNNAMES*'。  
  
> [!NOTE]
>  如需如何將 SAP 查詢的參數轉譯為 EXECQUERY 語法資訊，請參閱[轉譯 SAP 查詢參數為 EXECQUERY 命令](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md)。  
  
### <a name="framing-an-execquery-syntax"></a>框架 EXECQUERY 語法  
 框架 EXECQUERY 作業來執行 SAP 查詢的語法，取決於 SAP 系統，包括在 SAP 中定義每個參數值中定義查詢的方式。 如需如何執行 SAP 查詢的 EXECQUERY 語法資訊，請參閱[轉譯 SAP 查詢參數為 EXECQUERY 命令](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md)。  
  
### <a name="additional-considerations-while-using-the-execquery-operation"></a>其他考量而使用 EXECQUERY 作業  
 此區段會列出使用 EXECQUERY 陳述式時，您必須謹記在心的點[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。  
  
- 指定使用者群組、 工作區中和 VARIANT 的值會傳遞做為標準 SAP RFC RSAQ_REMOTE_QUERY_CALL 是。 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不會驗證指定這些參數的值。  
  
- EXECQUERY 作業所傳回的所有值都都屬於字串類型。  
  
- 查詢名稱、 使用者群組、 工作區中和變化的關鍵字不區分大小寫。 不過，參數名稱必須一律位於上方 caseP 這類@P1，@P2等等。例如：  
  
  ```  
  EXECQUERY xyz USERGROUP=’mygrp’, NOT @P1= 'somevalue'  
  ```  
  
   等同於  
  
  ```  
  EXECQUERY xyz uSERgROUP=’mygrp’, NOT @P1= 'somevalue'  
  ```  
  
- EXECQUERY 所支援的運算子為 >，<>、 =、 < =、 ！ =、 NOT、 BETWEEN 和。  
  
- EXECQUERY 作業不支援萬用字元。 例如，下列陳述式會提供預期的輸出：  
  
  ```  
  EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024',  @P1 = '0000003262',@P2 = 'La Quinta Hotel & Towers'  
  ```  
  
   不過，相同的查詢執行時未使用萬用字元會顯示錯誤。 請注意，使用萬用字元<strong>@P2</strong>。  
  
  ```  
  EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024',  @P1 = '0000003262',@P2 = '*&*'  
  ```  
  
   在此範例中，您可能會收到錯誤訊息指出找不資料。 這是因為查詢會搜尋 **'\*&\*'** 做為字串並不會視為星號 （*） 做為萬用字元。  
  
- 您一律必須指定日期值格式為 YYYYMMDD。  
  
- 如果您執行的具有 variant，SAP 系統中定義的查詢，您可以指定之變數的名稱做為命令的一部分。 例如：  
  
  ```  
  EXECQUERY myquery @usergroup='mygroup',@variant = 'variant1'  
  ```  
  
  > [!NOTE]
  >  您不需要指定變數的名稱，如果預設變數，會在 SAP 系統中定義的查詢。  
  
## <a name="see-also"></a>另請參閱  
 [使用 .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)