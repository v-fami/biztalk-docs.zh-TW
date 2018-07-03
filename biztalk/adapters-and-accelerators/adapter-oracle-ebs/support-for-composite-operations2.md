---
title: 支援複合 Operations2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3f65cf10-4e27-4872-bc6a-defe6cbab198
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 724d5bc41686abc3928716a0e08801107df25055
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979383"
---
# <a name="support-for-composite-operations"></a>支援複合作業
[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可讓配接器用戶端執行複合作業可包含任意數目的下列作業，並依照任何順序：  
  
- 選取、 插入、 更新和刪除作業的介面資料表和資料庫資料表。  
  
- 選取介面檢視和資料庫檢視上的作業。  
  
- 預存程序、 函數和內顯示為配接器中的作業的封裝的程序。  
  
  資料表和檢視表相同的資料庫或不同的資料庫中的複合運算中的作業可以為目標。 不過，資料無法共用，或在複合作業中的不同作業間重複使用。 比方說，在複合作業中，選取作業的結果集不能用於做為輸入參數的預存程序。  
  
  複合作業中的每項作業會使用個別的連接。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]取用 ODP.NET 連接集區的連線數目上限為在複合作業中，作業數目及取得執行的作業，然後再釋放連接。 不過，複合作業的作業會傳回結果集，如果連接已釋放，才使用訊息。  
  
> [!IMPORTANT]
>  如果您執行複合作業時遇到逾時問題則可能是因為連線的數目小於中複合作業牽涉到的作業數目：  
> 
> - 做為 OUT 包含 BFILE、 BLOB、 CLOB、 NCLOB、 和 REF CURSOR 的預存程序或在 OUT 參數。  
>   -   選取作業。  
> 
>   若要解決此問題，您必須確定有"n"這類的複合運算中的作業數目，為指定的值**MinPoolSize**繫結屬性是"n + 1"或更新版本。 如需詳細資訊**MinPoolSize**繫結屬性，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
 如需詳細資訊：  
  
- 如何執行中的複合作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[使用 BizTalk Server 的 Oracle 資料庫上執行複合作業](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md)。  
  
- 訊息複合作業的結構描述，請參閱[複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-composite-operation1.md)。  
  
> [!NOTE]
>  您也可以設定應用程式內容中的複合作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 它是必要設定複合作業的應用程式內容，如果任一項中複合作業的作業會在介面資料表或介面檢視上執行。 應用程式內容，以及如何將它設定的相關資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Oracle E-business Suite 配接器支援哪些作業](../../adapters-and-accelerators/adapter-oracle-ebs/what-operations-are-supported-by-the-oracle-e-business-suite-adapter.md)