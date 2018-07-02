---
title: LEXECUTE 作業的訊息結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLEXECUTE operations, message schemas for
ms.assetid: 744645f4-0674-44e0-bf8d-8df70086b0f1
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f753d2dcbd5782f456b099174e0369e37cca2e6f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981479"
---
# <a name="message-schemas-for-the-sqlexecute-operation"></a>LEXECUTE 作業的訊息結構描述
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] 呈現強型別 LOB 系統中的構件的中繼資料，並公開在這些成品的標準作業。 不過，有些，應用程式可能需要執行應用程式中的商務邏輯由任意 SQL 陳述式的情況。 例如，您可能想要：  
  
- 對資料庫成品是不會顯示所執行作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; 例如，取得 CURVAL 或 NEXTVAL 的 Oracle 序列。  
  
- 執行資料定義語言 」 作業;例如，建立資料表。  
  
- 在設計階段; 沒有為資料庫成品上執行作業比方說，更新您的商務邏輯所建立的暫存資料表中的記錄。  
  
- 執行資料表上更複雜的 DML 作業，所呈現的作業比[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; 的範例執行包含 JOIN 子句的查詢。  
  
  [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]呈現一種特殊的作業呼叫 SQLEXECUTE 作業，以支援這種情況。 藉由使用這項作業，您可以指定任意的 SQL 陳述式的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]Oracle 資料庫上執行。 您也可以指定多個輸入參數的 SQL 陳述式區塊。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]執行每個參數集一次的 SQL 陳述式，並傳回泛型 （弱型別） 資料錄集的任何輸出。  
  
> [!NOTE]
>  您可以傳遞中及在 OUT 參數，程序、 函數和 SQLEXECUTE 作業中的封裝。 叫用的成品將會執行以提供的 Oracle 資料庫中; 上的參數不過，在 SQLEXECUTE 作業不會傳回外的值和在 OUT 參數，用戶端。 如果您想要叫用程序、 函式或套件，Microsoft 建議您這麼做叫用專用的作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開 （expose) 這些 Oracle 成品。  
  
 下列 XML 顯示 SQLEXECUTE 作業的結構：  
  
```  
<SQLEXECUTE xmlns="SQLEXECUTE">  
  <SQLSTATEMENT> [STATEMENT] </SQLSTATEMENT>  
  <PARAMETERSCHEMA>[PARAM_SPEC]</PARAMETERSCHEMA>  
  <PARAMETERSET>  
    <PARAMETERDATA>  
      <PARAMETER xmlns:c="http://schemas.microsoft.com/2003/10/Serialization/Arrays">  
        <c:string>[PARAM_VAL_1]</c:string>  
      </PARAMETER>  
    </PARAMETERDATA>  
    …  
  </PARAMETERSET>  
</SQLEXECUTE>  
```  
  
 [陳述式] = SQL 陳述式執行;比方說，「 選取 * 從 emp WHERE empno =: emp_no"。  
  
 [PARAM_SPEC] = 在 SQL 陳述式和其資料類型，在參數清單例如，"emp_no 數目 」。  
  
 [PARAM_VAL_1] = 第一個參數的值。  
  
 每個\<PARAMETERDATA\>一節包含一組完整的\<參數\>符合結構描述中的項目\<PARAMETERSCHEMA\>一節。 \<PARAMETERSET\>可以包含多個\<PARAMETERDATA\>區段。 如果發生這種情況，SQL 陳述式執行多次，一次針對每個參數集。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Oracle Database 的訊息和訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)