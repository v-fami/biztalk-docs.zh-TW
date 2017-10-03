---
title: "使用 SQL 配接器在 BizTalk 中查詢通知訊息結構描述 |Microsoft 文件"
description: "使用 SQL 配接器從 SQL Server 資料庫中 BizTalk 接收查詢通知"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5183655-64d4-4767-a923-0a575e3708cd
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c78c817470bd8acd41f44204653c41e9012d154
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-query-notification"></a><span data-ttu-id="73f69-103">查詢通知的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="73f69-103">Message Schemas for Query Notification</span></span>
<span data-ttu-id="73f69-104">[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]呈現從 SQL Server 資料庫接收查詢通知的通知作業。</span><span class="sxs-lookup"><span data-stu-id="73f69-104">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] surfaces the Notification operation to receive query notifications from the SQL Server database.</span></span>  
  
 <span data-ttu-id="73f69-105">設定繫結屬性設定通知作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="73f69-105">You configure the Notification operation by setting binding properties in the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="73f69-106">如需通知相關的繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="73f69-106">For more information about the Notification-related binding properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="73f69-107">您設定**NotificationStatement**內容繫結至指定的 SQL 陳述式 (SELECT 或 EXEC\<預存程序 >) 的查詢通知。</span><span class="sxs-lookup"><span data-stu-id="73f69-107">You set the **NotificationStatement** binding property to specify a SQL statement (SELECT or EXEC \<stored procedure>) for the query notification.</span></span> <span data-ttu-id="73f69-108">此查詢的結果集傳回做為強型別資料通知作業中的程式碼時。</span><span class="sxs-lookup"><span data-stu-id="73f69-108">The result set of this query is returned as strongly-typed data to your code in the Notification operation.</span></span>  
  
## <a name="message-structure-for-the-notification-operation"></a><span data-ttu-id="73f69-109">通知作業的訊息結構</span><span class="sxs-lookup"><span data-stu-id="73f69-109">Message Structure for the Notification operation</span></span>  
 <span data-ttu-id="73f69-110">下表顯示通知作業的 XML 訊息結構。</span><span class="sxs-lookup"><span data-stu-id="73f69-110">The following table shows the XML message structure for the Notification operation.</span></span>  

<span data-ttu-id="73f69-111">**作業**:`Notification`</span><span class="sxs-lookup"><span data-stu-id="73f69-111">**Operation**: `Notification`</span></span>

<span data-ttu-id="73f69-112">**XML 訊息**:</span><span class="sxs-lookup"><span data-stu-id="73f69-112">**XML message**:</span></span>  
```xml
<?xml version="1.0" encoding="utf-8" ?>
  <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification">
    <Info>Value</Info>
    <Source>Value</Source>
    <Type>Value</Type>
 </Notification>
```

<span data-ttu-id="73f69-113">**描述**： 這是 SQL Server 傳送到配接器用戶端的傳入的訊息。</span><span class="sxs-lookup"><span data-stu-id="73f69-113">**Description**: This is the inbound message that is sent by the SQL Server to the adapter clients.</span></span> <span data-ttu-id="73f69-114">在訊息：</span><span class="sxs-lookup"><span data-stu-id="73f69-114">In the message:</span></span>

- <span data-ttu-id="73f69-115">`<Info>`標記指出通知的原因。</span><span class="sxs-lookup"><span data-stu-id="73f69-115">The `<Info>` tag indicates the reason for the notification.</span></span> <span data-ttu-id="73f69-116">例如，這個標記中的 「 插入 」 值表示已在一或多個通知的陳述式中參考的資料表中插入資料。</span><span class="sxs-lookup"><span data-stu-id="73f69-116">For example, an “insert” value in this tag indicates that data has been inserted in one or more of the tables referenced in the notification statement.</span></span>
- <span data-ttu-id="73f69-117">`<Source>`標記表示的通知來源。</span><span class="sxs-lookup"><span data-stu-id="73f69-117">The `<Source>` tag indicates the source for the notification.</span></span> <span data-ttu-id="73f69-118">例如，這個標記中的 「 資料 」 值表示參考的物件中的資料的變更。</span><span class="sxs-lookup"><span data-stu-id="73f69-118">For example, a “data” value in this tag indicates a change in the data in a referenced object.</span></span> <span data-ttu-id="73f69-119">同樣地，這個標記中的 「 物件 」 值表示參考物件的變更。</span><span class="sxs-lookup"><span data-stu-id="73f69-119">Similarly, an “object” value in this tag indicates a change in a referenced object.</span></span>
- <span data-ttu-id="73f69-120">`<Type>`標記表示的資料變更類型。</span><span class="sxs-lookup"><span data-stu-id="73f69-120">The `<Type>` tag indicates the type of data change.</span></span> <span data-ttu-id="73f69-121">查詢通知訊息有兩種類型： 變更和訂閱。</span><span class="sxs-lookup"><span data-stu-id="73f69-121">Query notification messages are of two types: change and subscribe.</span></span> <span data-ttu-id="73f69-122">A 的 「 變更 」 中的值`<Type>`標記表示查詢的結果已變更，而在 「 訂閱 」 值`<Type>`標記表示的訂用帳戶要求失敗。</span><span class="sxs-lookup"><span data-stu-id="73f69-122">A “change” value in the `<Type>` tag indicates that the results of the query have changed, whereas a “subscribe” value in the `<Type>` tag indicates that a subscription request failed.</span></span>

  
## <a name="message-action-for-the-notification-operation"></a><span data-ttu-id="73f69-123">通知作業的訊息動作</span><span class="sxs-lookup"><span data-stu-id="73f69-123">Message Action for the Notification Operation</span></span>  
 <span data-ttu-id="73f69-124">通知作業的訊息動作是 「 通知 」。</span><span class="sxs-lookup"><span data-stu-id="73f69-124">The message action for the notification operation is “Notification.”</span></span>  
  