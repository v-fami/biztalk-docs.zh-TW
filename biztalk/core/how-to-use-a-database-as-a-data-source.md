---
title: 如何使用做為資料來源的資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Business Rule Composer, data sources
ms.assetid: a68057ed-836f-499f-bb80-f644d81bcfc5
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3a9201ee729288a819a3d527a6ecb4fefd32797
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255710"
---
# <a name="how-to-use-a-database-as-a-data-source"></a><span data-ttu-id="ea40e-102">如何將資料庫做為資料來源使用</span><span class="sxs-lookup"><span data-stu-id="ea40e-102">How to Use a Database as a Data Source</span></span>
<span data-ttu-id="ea40e-103">您可以將資料庫指定為資料來源。</span><span class="sxs-lookup"><span data-stu-id="ea40e-103">You can specify a database as a data source.</span></span> <span data-ttu-id="ea40e-104">然後，您可以從資料庫中選取資料表或資料行，並將其拖曳至某個詞彙定義或規則，以作為事實使用。</span><span class="sxs-lookup"><span data-stu-id="ea40e-104">You can subsequently select a table or table column from the database, and drag it onto a vocabulary definition or rule to use as a fact.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea40e-105">您可以選擇繫結至資料庫資料列/資料表使用**DataConnection**或**TypedDataTable**藉由選取 [資料連線 」 或 「 資料庫資料表/資料列 」 從**資料庫繫結型別** [屬性] 視窗中的下拉式清單方塊**資料庫**事實總管] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ea40e-105">You can choose to bind to the database row/table using either **DataConnection** or **TypedDataTable** by selecting "Data connection" or "Database table/row" from the **Database binding type** drop-down box in the Property Window for the **Databases** tab of Fact Explorer.</span></span> <span data-ttu-id="ea40e-106">**DataConnection**預設會使用繫結。</span><span class="sxs-lookup"><span data-stu-id="ea40e-106">**DataConnection** binding is used by default.</span></span>  
  
### <a name="to-specify-a-sql-database-as-a-data-source"></a><span data-ttu-id="ea40e-107">將 SQL 資料庫指定為資料來源</span><span class="sxs-lookup"><span data-stu-id="ea40e-107">To specify a SQL database as a data source</span></span>  
  
1.  <span data-ttu-id="ea40e-108">在 事實總管 視窗中，按一下**資料庫** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ea40e-108">In the Facts Explorer window, click the **Databases** tab.</span></span>  
  
2.  <span data-ttu-id="ea40e-109">以滑鼠右鍵按一下**伺服器**節點，然後再按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="ea40e-109">Right-click the **Servers** node, and then click **Browse**.</span></span>  
  
3.  <span data-ttu-id="ea40e-110">在下拉式清單中選取可用的資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="ea40e-110">In the drop-down list, select an available database server.</span></span>  
  
4.  <span data-ttu-id="ea40e-111">選取驗證類型。</span><span class="sxs-lookup"><span data-stu-id="ea40e-111">Select an authentication type.</span></span> <span data-ttu-id="ea40e-112">若您選擇 SQL 驗證，請輸入登入名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="ea40e-112">If you select SQL authentication, enter a logon name and password.</span></span> <span data-ttu-id="ea40e-113">當您輸入驗證資訊時，請按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ea40e-113">When you have entered your authentication information, click **OK**.</span></span>  
  
     <span data-ttu-id="ea40e-114">![資料庫樹狀結構瀏覽器的螢幕擷取畫面。](../core/media/ebiz-dbbrows.gif "ebiz_dbbrows")</span><span class="sxs-lookup"><span data-stu-id="ea40e-114">![Screenshot of databases of tree brower.](../core/media/ebiz-dbbrows.gif "ebiz_dbbrows")</span></span>  
<span data-ttu-id="ea40e-115">瀏覽資料庫</span><span class="sxs-lookup"><span data-stu-id="ea40e-115">Browsing a database</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea40e-116">不支援 SQL Server 資料庫檢視。</span><span class="sxs-lookup"><span data-stu-id="ea40e-116">SQL Server database views are not supported.</span></span>