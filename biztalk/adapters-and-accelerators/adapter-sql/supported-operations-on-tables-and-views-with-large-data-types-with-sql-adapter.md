---
title: 資料表和檢視表包含使用 SQL 配接器的大型資料類型的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70f3b863-da3c-45b0-98f2-469a62286ebf
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4f693b676c1e3c0675051e9d0faf685e8b9d8df
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021186"
---
# <a name="operations-on-tables-and-views-that-contain-large-data-types-using-the-sql-adapter"></a>資料表和檢視表包含使用 SQL 配接器的大型資料類型的作業
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]提供支援下列 SQL Server 的大型資料類型：  
  
- Varchar （max)  
  
- Nvarchar （max)  
  
- Varbinary （max)  
  
  從 SQL Server 讀取大型資料值[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開 （expose) 選取的作業。  
  
  若要將大型資料值寫入至 SQL Server，[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開設定 < column_name > 作業，其中 < column_name > 是類型 varchar （max）、 nvarchar （max） 或 varbinary （max） 資料行的名稱。 設定 < column_name > 作業也可讓配接器來寫入 SQL Server 2008 中的 FILESTREAM 資料的用戶端。  
  
> [!NOTE]
>  設定 < column_name > 作業是只適用於這些資料表和檢視表包含資料行與先前所述的三個大型資料任何的類型項目。  
  
 如需執行包含大型資料類型的 SQL Server 中的資料表和檢視表上的作業的詳細資訊，請參閱[資料表和檢視表包含使用 SQL 配接器的大型資料類型的作業](../../adapters-and-accelerators/adapter-sql/supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
 [連接到 SAP 系統使用配接器](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)