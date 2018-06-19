---
title: BFILE 資料型別，Oracle 資料庫中之資料表上的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- operations, on tables with BFILE data types
- BFILE data type
- BFILE
ms.assetid: 7937564e-4423-459f-9824-6a27113ebfb3
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c236651e6c44248ea8f6cf0f73f0c9bc17e46ac5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214310"
---
# <a name="operations-on-tables-with-bfile-data-types-in-oracle-database"></a>BFILE 資料型別，Oracle 資料庫中之資料表上的作業
[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]資料表和預存程序中支援 BFILE 資料型別。 下表摘要說明根據執行的作業，配接器所公開的 BFILE 資料型別和 LOB 成品 （資料表/程序） 存取：  
  
|成品|作業|BFILE 資料行/參數為公開的資料類型|註解|  
|--------------|---------------|--------------------------------------------|--------------|  
|TABLE|INSERT|字串|表示要插入至 BFILE 資料行之檔案的邏輯 Oracle 目錄路徑<br /><br /> 例如 MYDIR/screen.jpg MYDIR 其中是在 Oracle 中的邏輯目錄|  
|TABLE|UPDATE|字串|表示更新成 BFILE 資料行之檔案的邏輯 Oracle 目錄路徑|  
|TABLE|SELECT|byte[]|代表從屬 BFILE 的二進位資料|  
|預存程序|PARAM 中|字串|表示要插入至 BFILE 資料行之檔案的邏輯 Oracle 目錄路徑<br /><br /> 例如 MYDIR/screen.jpg MYDIR 其中是在 Oracle 中的邏輯目錄|  
|預存程序|OUT 參數|字串|表示要插入至 BFILE 資料行之檔案的邏輯 Oracle 目錄路徑<br /><br /> 例如 MYDIR/screen.jpg MYDIR 其中是在 Oracle 中的邏輯目錄|  
|預存程序|INOUT 參數|不支援|-|  
  
 也支援特殊作業 ReadLOB BFILE 資料型別之資料表上。 不支援 UpdateLOB 作業。 或者，配接器用戶端可以使用更新作業。  
  
 如需詳細資訊：  
  
-   使用包含 BFILE 資料型別資料表上執行的作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[以 BFILE 資料型別使用 BizTalk Server 的 Oracle 資料庫中執行的資料表作業](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-bfile-data-types-in-oracle-db-using-biztalk.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)