---
title: "訊息結構描述的通知 Operation1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f98d76d0-6084-4de7-b6ff-124202ca92ab
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd0d7513a0a439d34d5bfb4722fec2b9025e676b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-the-notification-operation"></a><span data-ttu-id="742b7-102">通知作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="742b7-102">Message Schemas for the Notification Operation</span></span>
<span data-ttu-id="742b7-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]介面上接收從 Oracle 資料庫的資料庫變更通知的通知作業。</span><span class="sxs-lookup"><span data-stu-id="742b7-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces the Notification operation to receive database change notifications from the Oracle database.</span></span>  
  
 <span data-ttu-id="742b7-104">設定繫結屬性設定通知作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="742b7-104">You configure the Notification operation by setting binding properties in the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="742b7-105">如需通知相關的繫結屬性的詳細資訊，請參閱[閱讀有關 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="742b7-105">For more information about the Notification-related binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span> <span data-ttu-id="742b7-106">您設定**NotificationStatement**內容繫結至指定的查詢通知的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="742b7-106">You set the **NotificationStatement** binding property to specify a SELECT statement for the query notification.</span></span>  
  
## <a name="message-structure-for-the-notification-operation"></a><span data-ttu-id="742b7-107">通知作業的訊息結構</span><span class="sxs-lookup"><span data-stu-id="742b7-107">Message Structure for the Notification Operation</span></span>  
 <span data-ttu-id="742b7-108">下表顯示通知作業的 XML 訊息結構。</span><span class="sxs-lookup"><span data-stu-id="742b7-108">The following table shows the XML message structure for the Notification operation.</span></span>  
  
|<span data-ttu-id="742b7-109">作業</span><span class="sxs-lookup"><span data-stu-id="742b7-109">Operation</span></span>|<span data-ttu-id="742b7-110">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="742b7-110">XML Message</span></span>|<span data-ttu-id="742b7-111">Description</span><span class="sxs-lookup"><span data-stu-id="742b7-111">Description</span></span>|  
|---------------|-----------------|-----------------|  
|<span data-ttu-id="742b7-112">通知</span><span class="sxs-lookup"><span data-stu-id="742b7-112">Notification</span></span>|`<?xml version="1.0" encoding="utf-8" ?>  <Notification xmlns="http://Microsoft.LobServices.OracleDB/2007/03/Notification">    <Info>Value</Info>    <Source>Value</Source>    <Type>Value</Type> </Notification>`|<span data-ttu-id="742b7-113">這是 Oracle 資料庫傳送到配接器用戶端的傳入的訊息。</span><span class="sxs-lookup"><span data-stu-id="742b7-113">This is the inbound message that is sent by the Oracle database to the adapter clients.</span></span> <span data-ttu-id="742b7-114">在訊息：</span><span class="sxs-lookup"><span data-stu-id="742b7-114">In the message:</span></span><br /><br /> <span data-ttu-id="742b7-115">-`<Info>`標記指出通知的原因。</span><span class="sxs-lookup"><span data-stu-id="742b7-115">- The `<Info>` tag indicates the reason for the notification.</span></span> <span data-ttu-id="742b7-116">例如，這個標記中的 「 插入 」 值表示已在一或多個通知的陳述式中參考的資料表中插入資料。</span><span class="sxs-lookup"><span data-stu-id="742b7-116">For example, an “insert” value in this tag indicates that data has been inserted in one or more of the tables referenced in the notification statement.</span></span><br /><br /> <span data-ttu-id="742b7-117">-`<Source>`標記表示的通知來源。</span><span class="sxs-lookup"><span data-stu-id="742b7-117">- The `<Source>` tag indicates the source for the notification.</span></span> <span data-ttu-id="742b7-118">例如，這個標記中的 「 資料 」 值表示參考的物件中的資料的變更。</span><span class="sxs-lookup"><span data-stu-id="742b7-118">For example, a “data” value in this tag indicates a change in the data in a referenced object.</span></span> <span data-ttu-id="742b7-119">同樣地，這個標記中的 「 物件 」 值表示參考物件的變更。</span><span class="sxs-lookup"><span data-stu-id="742b7-119">Similarly, an “object” value in this tag indicates a change in a referenced object.</span></span><br /><br /> <span data-ttu-id="742b7-120">-`<Type>`標記表示的資料變更類型。</span><span class="sxs-lookup"><span data-stu-id="742b7-120">- The `<Type>` tag indicates the type of data change.</span></span> <span data-ttu-id="742b7-121">例如，「 更新 」 值中`<Type>`標記代表查詢的結果已更新。</span><span class="sxs-lookup"><span data-stu-id="742b7-121">For example, an “Update” value in the `<Type>` tag indicates that the results of the query have been updated.</span></span>|  
  
## <a name="message-action-for-the-notification-operation"></a><span data-ttu-id="742b7-122">通知作業的訊息動作</span><span class="sxs-lookup"><span data-stu-id="742b7-122">Message Action for the Notification Operation</span></span>  
 <span data-ttu-id="742b7-123">通知作業的訊息動作是 「 http://Microsoft.LobServices.OracleDB/2007/03/Notification"。</span><span class="sxs-lookup"><span data-stu-id="742b7-123">The message action for the notification operation is “http://Microsoft.LobServices.OracleDB/2007/03/Notification”.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="742b7-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="742b7-124">See Also</span></span>  
 [<span data-ttu-id="742b7-125">訊息和訊息結構描述，BizTalk adapter for Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="742b7-125">Messages and Message Schemas for BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)