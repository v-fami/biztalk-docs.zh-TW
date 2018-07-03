---
title: 對具有 BFILE 資料類型，Oracle 資料庫中的資料表上的作業 |Microsoft Docs
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
ms.openlocfilehash: ab9885497468f91b309eb51ac0abbf4c0807ca76
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998255"
---
# <a name="operations-on-tables-with-bfile-data-types-in-oracle-database"></a>對具有 BFILE 資料類型，Oracle 資料庫中的資料表上的作業
[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]資料表和預存程序中支援 BFILE 資料型別。 下表摘要說明根據執行的作業，配接器所公開的 BFILE 資料類型和存取 LOB 成品 （資料表/程序）：  
  
|成品|作業|BFILE 資料行/參數為公開的資料類型|註解|  
|--------------|---------------|--------------------------------------------|--------------|  
|TABLE|Insert|String|表示要插入到 BFILE 資料行之檔案的邏輯的 Oracle 目錄路徑<br /><br /> 例如 MYDIR/screen.jpg MYDIR 其中是在 Oracle 中的邏輯目錄|  
|TABLE|UPDATE|String|至檔案，以更新到 BFILE 資料行代表邏輯的 Oracle 目錄路徑|  
|TABLE|SELECT|byte[]|代表構成 BFILE 的二進位資料|  
|預存程序|在 參數|String|表示要插入到 BFILE 資料行之檔案的邏輯的 Oracle 目錄路徑<br /><br /> 例如 MYDIR/screen.jpg MYDIR 其中是在 Oracle 中的邏輯目錄|  
|預存程序|OUT 參數|String|表示要插入到 BFILE 資料行之檔案的邏輯的 Oracle 目錄路徑<br /><br /> 例如 MYDIR/screen.jpg MYDIR 其中是在 Oracle 中的邏輯目錄|  
|預存程序|INOUT 參數|不支援|-|  
  
 BFILE 資料型別之資料表上也支援特殊作業 ReadLOB。 不支援 UpdateLOB 作業。 配接器用戶端，或者可以使用更新作業。  
  
 如需詳細資訊：  
  
- 使用包含 BFILE 資料類型的資料表上執行的作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 具有 BFILE 資料類型，使用 BizTalk Server 的 Oracle 資料庫中的資料表執行作業](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-bfile-data-types-in-oracle-db-using-biztalk.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)