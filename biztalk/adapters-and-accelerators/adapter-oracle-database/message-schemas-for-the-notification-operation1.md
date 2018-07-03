---
title: 針對通知 Operation1 訊息結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f98d76d0-6084-4de7-b6ff-124202ca92ab
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cdf371335a1242423c4497f186fa5764f5b2fb2f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991687"
---
# <a name="message-schemas-for-the-notification-operation"></a><span data-ttu-id="c6d5b-102">通知作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="c6d5b-102">Message Schemas for the Notification Operation</span></span>
<span data-ttu-id="c6d5b-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現通知作業，若要從 Oracle 資料庫接收資料庫變更通知。</span><span class="sxs-lookup"><span data-stu-id="c6d5b-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces the Notification operation to receive database change notifications from the Oracle database.</span></span>  
  
 <span data-ttu-id="c6d5b-104">您藉由設定繫結屬性設定通知作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c6d5b-104">You configure the Notification operation by setting binding properties in the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="c6d5b-105">如需有關的通知相關的繫結屬性的詳細資訊，請參閱[了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c6d5b-105">For more information about the Notification-related binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span> <span data-ttu-id="c6d5b-106">您設定**NotificationStatement**繫結屬性，以指定的查詢通知的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c6d5b-106">You set the **NotificationStatement** binding property to specify a SELECT statement for the query notification.</span></span>  
  
## <a name="message-structure-for-the-notification-operation"></a><span data-ttu-id="c6d5b-107">通知作業的訊息結構</span><span class="sxs-lookup"><span data-stu-id="c6d5b-107">Message Structure for the Notification Operation</span></span>  
 <span data-ttu-id="c6d5b-108">下表顯示通知作業的 XML 訊息結構。</span><span class="sxs-lookup"><span data-stu-id="c6d5b-108">The following table shows the XML message structure for the Notification operation.</span></span>  
  
|<span data-ttu-id="c6d5b-109">作業</span><span class="sxs-lookup"><span data-stu-id="c6d5b-109">Operation</span></span>|<span data-ttu-id="c6d5b-110">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="c6d5b-110">XML Message</span></span>|<span data-ttu-id="c6d5b-111">描述</span><span class="sxs-lookup"><span data-stu-id="c6d5b-111">Description</span></span>|  
|---------------|-----------------|-----------------|  
|<span data-ttu-id="c6d5b-112">通知</span><span class="sxs-lookup"><span data-stu-id="c6d5b-112">Notification</span></span>|`<?xml version="1.0" encoding="utf-8" ?>  <Notification xmlns="http://Microsoft.LobServices.OracleDB/2007/03/Notification">    <Info>Value</Info>    <Source>Value</Source>    <Type>Value</Type> </Notification>`|<span data-ttu-id="c6d5b-113">這是 Oracle 資料庫傳送到配接器用戶端的傳入的訊息。</span><span class="sxs-lookup"><span data-stu-id="c6d5b-113">This is the inbound message that is sent by the Oracle database to the adapter clients.</span></span> <span data-ttu-id="c6d5b-114">在 訊息：</span><span class="sxs-lookup"><span data-stu-id="c6d5b-114">In the message:</span></span><br /><br /> <span data-ttu-id="c6d5b-115">-`<Info>`標記指出通知的原因。</span><span class="sxs-lookup"><span data-stu-id="c6d5b-115">- The `<Info>` tag indicates the reason for the notification.</span></span> <span data-ttu-id="c6d5b-116">比方說，這個標記中的"insert"值會指出已在一或多個通知的陳述式中參考的資料表中插入資料。</span><span class="sxs-lookup"><span data-stu-id="c6d5b-116">For example, an “insert” value in this tag indicates that data has been inserted in one or more of the tables referenced in the notification statement.</span></span><br /><br /> <span data-ttu-id="c6d5b-117">-`<Source>`標記表示通知的來源。</span><span class="sxs-lookup"><span data-stu-id="c6d5b-117">- The `<Source>` tag indicates the source for the notification.</span></span> <span data-ttu-id="c6d5b-118">比方說，「 資料 」 值，這個標記中的表示受參考的物件中的資料的變更。</span><span class="sxs-lookup"><span data-stu-id="c6d5b-118">For example, a “data” value in this tag indicates a change in the data in a referenced object.</span></span> <span data-ttu-id="c6d5b-119">同樣地，這個標記中的 「 物件 」 值會指出參考的物件中的變更。</span><span class="sxs-lookup"><span data-stu-id="c6d5b-119">Similarly, an “object” value in this tag indicates a change in a referenced object.</span></span><br /><br /> <span data-ttu-id="c6d5b-120">-`<Type>`標記表示資料變更的類型。</span><span class="sxs-lookup"><span data-stu-id="c6d5b-120">- The `<Type>` tag indicates the type of data change.</span></span> <span data-ttu-id="c6d5b-121">「 更新 」 中的值，例如`<Type>`標記代表查詢的結果，已更新。</span><span class="sxs-lookup"><span data-stu-id="c6d5b-121">For example, an “Update” value in the `<Type>` tag indicates that the results of the query have been updated.</span></span>|  
  
## <a name="message-action-for-the-notification-operation"></a><span data-ttu-id="c6d5b-122">通知作業的訊息動作</span><span class="sxs-lookup"><span data-stu-id="c6d5b-122">Message Action for the Notification Operation</span></span>  
 <span data-ttu-id="c6d5b-123">通知作業的訊息動作是 「<http://Microsoft.LobServices.OracleDB/2007/03/Notification”>。</span><span class="sxs-lookup"><span data-stu-id="c6d5b-123">The message action for the notification operation is “<http://Microsoft.LobServices.OracleDB/2007/03/Notification”>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6d5b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6d5b-124">See Also</span></span>  
 [<span data-ttu-id="c6d5b-125">BizTalk Adapter for Oracle Database 的訊息和訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="c6d5b-125">Messages and Message Schemas for BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)