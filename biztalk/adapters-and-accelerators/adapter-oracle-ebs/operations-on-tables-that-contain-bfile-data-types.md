---
title: 資料表包含 BFILE 資料型別上的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0d7ebeb9-c2d6-4024-a169-263b947eeeb1
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5096539b86512e51756d3a872ff566872ff520f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25960996"
---
# <a name="operations-on-tables-that-contain-bfile-data-types"></a>資料表包含 BFILE 資料型別上的作業
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]資料表和預存程序中支援 BFILE 資料型別。 

## <a name="bfile-data-types"></a>BFILE 資料型別
下表摘要說明根據執行的作業，配接器所公開的 BFILE 資料型別和 LOB 成品 （資料表/程序） 存取：  
  
|成品|作業|BFILE 資料行/參數為公開的資料類型|註解|  
|--------------|---------------|--------------------------------------------|--------------|  
|TABLE|INSERT|字串|表示要插入至 BFILE 資料行之檔案的邏輯 Oracle 目錄路徑<br /><br /> 例如 MYDIR/screen.jpg MYDIR 其中是在 Oracle 中的邏輯目錄|  
|TABLE|UPDATE|字串|表示更新成 BFILE 資料行之檔案的邏輯 Oracle 目錄路徑|  
|TABLE|SELECT|byte[]|代表從屬 BFILE 的二進位資料|  
|預存程序|PARAM 中|字串|表示要插入至 BFILE 資料行之檔案的邏輯 Oracle 目錄路徑<br /><br /> 例如 MYDIR/screen.jpg MYDIR 其中是在 Oracle 中的邏輯目錄|  
|預存程序|OUT 參數|字串|表示要插入至 BFILE 資料行之檔案的邏輯 Oracle 目錄路徑<br /><br /> 例如 MYDIR/screen.jpg MYDIR 其中是在 Oracle 中的邏輯目錄|  
|預存程序|INOUT 參數|不支援|-|  
  
 特殊作業`Read_<LOBColName>`BFILE 資料型別，與資料表上也支援其中\<LOBColName\>是資料表中的 LOB 資料行名稱。 `Update_<LOBColName>` BFILE 資料型別不支援作業。 或者，配接器用戶端可以使用更新作業。  
  
## <a name="more-good-info"></a>良好的詳細資訊  
  
-   `Read_<LOBColName>`和`Update_<LOBColName>`作業，請參閱[介面資料表、 介面檢視、 資料表和檢視表，包含 LOB 資料的作業](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md)。  
  
## <a name="see-also"></a>請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)