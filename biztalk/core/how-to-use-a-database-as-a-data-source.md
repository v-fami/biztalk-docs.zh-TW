---
title: "如何使用做為資料來源的資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Business Rule Composer, data sources
ms.assetid: a68057ed-836f-499f-bb80-f644d81bcfc5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3a9201ee729288a819a3d527a6ecb4fefd32797
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-a-database-as-a-data-source"></a>如何將資料庫做為資料來源使用
您可以將資料庫指定為資料來源。 然後，您可以從資料庫中選取資料表或資料行，並將其拖曳至某個詞彙定義或規則，以作為事實使用。  
  
> [!NOTE]
>  您可以選擇繫結至資料庫資料列/資料表使用**DataConnection**或**TypedDataTable**藉由選取 [資料連線 」 或 「 資料庫資料表/資料列 」 從**資料庫繫結型別** [屬性] 視窗中的下拉式清單方塊**資料庫**事實總管] 索引標籤。 **DataConnection**預設會使用繫結。  
  
### <a name="to-specify-a-sql-database-as-a-data-source"></a>將 SQL 資料庫指定為資料來源  
  
1.  在 事實總管 視窗中，按一下**資料庫** 索引標籤。  
  
2.  以滑鼠右鍵按一下**伺服器**節點，然後再按一下**瀏覽**。  
  
3.  在下拉式清單中選取可用的資料庫伺服器。  
  
4.  選取驗證類型。 若您選擇 SQL 驗證，請輸入登入名稱和密碼。 當您輸入驗證資訊時，請按一下**確定**。  
  
     ![資料庫樹狀結構瀏覽器的螢幕擷取畫面。] (../core/media/ebiz-dbbrows.gif "ebiz_dbbrows")  
瀏覽資料庫  
  
> [!NOTE]
>  不支援 SQL Server 資料庫檢視。