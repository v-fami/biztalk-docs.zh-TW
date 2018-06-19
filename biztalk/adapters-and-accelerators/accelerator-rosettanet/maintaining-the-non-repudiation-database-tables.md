---
title: 維護不可否認性資料庫資料表 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- databases, purging
- databases, non-repudiation database
- maintaining databases, purging
- purging databases
- databases, maintaining
- non-repudiation, database
ms.assetid: 29222510-325b-4cd7-854b-6f548a63fd08
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 182172eccddcaad684f35335708dce6027fb111f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22210606"
---
# <a name="maintaining-the-non-repudiation-database-tables"></a><span data-ttu-id="fd5a3-102">維護不可否認性資料庫資料表</span><span class="sxs-lookup"><span data-stu-id="fd5a3-102">Maintaining the Non-Repudiation Database Tables</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="fd5a3-103">[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]存放在 BTARNArchive 資料庫的 MessageStorageIn 和 MessageStorageOut 資料表中的不可否認性目的的訊息。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-103"> [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] stores messages for non-repudiation purposes in the MessageStorageIn and MessageStorageOut tables of the BTARNArchive database.</span></span> <span data-ttu-id="fd5a3-104">這些資料表中的許多訊息可能會影響系統效能。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-104">Many messages in these tables can affect system performance.</span></span> <span data-ttu-id="fd5a3-105">如有必要，您可能需要定期清除和封存這些資料表中的訊息，以維護這些不可否認性資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-105">You may want to maintain these non-repudiation database tables by periodically purging and archiving messages from these tables, as appropriate.</span></span>  
  
## <a name="routine-database-maintenance"></a><span data-ttu-id="fd5a3-106">資料庫日常維護</span><span class="sxs-lookup"><span data-stu-id="fd5a3-106">Routine Database Maintenance</span></span>  
 <span data-ttu-id="fd5a3-107">當[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]收到訊息時，它一律會將訊息儲存在 MessageStorageIn 資料表，並設定初始**ToBePurged**欄位設為"1"，這表示訊息不需要不可否認性。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-107">When [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] receives a message, it always saves the message in the MessageStorageIn table and initially sets the **ToBePurged** field to "1", which indicates that the message does not require non-repudiation.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="fd5a3-108">然後解密，並將解碼的訊息，以判斷協議為何。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-108"> then decrypts and decodes the message to determine what the agreement is.</span></span> <span data-ttu-id="fd5a3-109">解密與解碼之後，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會檢視協議，決定是否必須以不可否認性目的來儲存訊息。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-109">After decrypting and decoding, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] examines the agreement to see whether it must save the message for non-repudiation purposes.</span></span> <span data-ttu-id="fd5a3-110">因此，它會設定如果**ToBePurged**欄位設為"0"，並填入訊息的其他欄位。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-110">If so, it sets the **ToBePurged** field to "0" and fills in the other fields of the message.</span></span> <span data-ttu-id="fd5a3-111">如果沒有，它會維持**ToBePurged**欄位為"1"並不填入訊息的其他欄位。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-111">If not, it leaves the **ToBePurged** field as "1" and does not fill in the other fields of the message.</span></span>  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="fd5a3-112">不會自動刪除訊息**ToBePurged**欄位設定為"1"。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-112"> does not automatically delete messages with the **ToBePurged** field set to "1".</span></span> <span data-ttu-id="fd5a3-113">此外，它也不會將以不可否認性目的儲存的訊息封存至其他資料表。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-113">In addition, it does not archive messages saved for non-repudiation to other tables.</span></span> <span data-ttu-id="fd5a3-114">這兩類訊息會在 MessageStorageIn 資料表中逐漸累積，進而影響效能。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-114">These two sets of messages can build up in the MessageStorageIn table and affect performance.</span></span> <span data-ttu-id="fd5a3-115">在資料庫的例行性維護工作中，您可能需要執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="fd5a3-115">As part of routine maintenance on the database, you may want to do the following:</span></span>  
  
-   <span data-ttu-id="fd5a3-116">執行預存程序包含下列 SQL 陳述式來刪除所有訊息於 MessageStorageIn 資料表其**ToBePurged**欄位是否不等於"0":</span><span class="sxs-lookup"><span data-stu-id="fd5a3-116">Run a stored procedure containing the following SQL statement to delete all messages in the MessageStorageIn table whose **ToBePurged** field is not equal to "0":</span></span>  
  
    ```  
    delete MessageStorageIn where ToBePurged <> 0  
    ```  
  
-   <span data-ttu-id="fd5a3-117">在經過一段適當的時間 (由公司原則所決定) 之後，執行預存程序，以便將不可否認性的訊息封存至不會影響效能的離線資料庫。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-117">After an appropriate period (which company policy may dictate), run a stored procedure to archive non-repudiation messages to an offline database that will not affect performance.</span></span> <span data-ttu-id="fd5a3-118">您可以使用，以判斷這段期間**TimeCreated** MessageStorageIn 資料表中的欄位。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-118">You can determine this period by using the **TimeCreated** field in the MessageStorageIn table.</span></span> <span data-ttu-id="fd5a3-119">訊息的不可否認性期限到期之後，您可以從封存資料庫刪除訊息，使用下列 SQL 陳述式 （這會刪除超過七日的訊息）：</span><span class="sxs-lookup"><span data-stu-id="fd5a3-119">After the non-repudiation period for a message has expired, you can delete the message from the archive database by using the following SQL statement (which deletes messages that are older than seven days):</span></span>  
  
    ```  
    delete <archive table name> where datediff(d, TimeCreated, GetUTCDATA())>7  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="fd5a3-120">**TimeCreated** MessageStorageIn 資料表中的欄位是使用 utc 格式。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-120">The **TimeCreated** field in the MessageStorageIn table is in UTC.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd5a3-121">您不應該刪除過去一小時之內收到的內送訊息。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-121">You should not delete an incoming message that is less than one hour old.</span></span>  
  
 <span data-ttu-id="fd5a3-122">當 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 傳送外寄訊息時，會先存取不可否認性協議。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-122">When [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] sends an outgoing message, it has access to the non-repudiation agreement.</span></span> <span data-ttu-id="fd5a3-123">如果協議要求不可否認性，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 就會將訊息儲存在 MessageStorageOut 資料表中。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-123">If the agreement requires non-repudiation, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] saves the message in the MessageStorageOut table.</span></span> <span data-ttu-id="fd5a3-124">如果沒有此要求，則不會將訊息儲存在資料表內。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-124">If not, it does not save the message in the table.</span></span> <span data-ttu-id="fd5a3-125">這表示沒有不需要**ToBePurged**本表中的欄位。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-125">This means that there is no need for a **ToBePurged** field in this table.</span></span> <span data-ttu-id="fd5a3-126">MessageStorageOut 資料表需要的唯一維護動作，便是在經過一段適當的時間後，將不可否認性訊息封存至離線資料庫，並在超過不可否認性時段後刪除每個訊息。</span><span class="sxs-lookup"><span data-stu-id="fd5a3-126">The only maintenance required for the MessageStorageOut table is to archive non-repudiation messages to an offline database after an appropriate period, and to delete each message after its non-repudiation period has expired.</span></span> <span data-ttu-id="fd5a3-127">若要如此，可利用下列 SQL 陳述式 (刪除超過七日的訊息)：</span><span class="sxs-lookup"><span data-stu-id="fd5a3-127">You can do so with the following SQL statement (which deletes messages that are older than seven days):</span></span>  
  
```  
delete MessageStorageOut where datediff(d, TimeCreated, GetUTCDATA())>7  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd5a3-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd5a3-128">See Also</span></span>  
 <span data-ttu-id="fd5a3-129">[RNIF 訊息處理](../../adapters-and-accelerators/accelerator-rosettanet/rnif-message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="fd5a3-129">[RNIF Message Processing](../../adapters-and-accelerators/accelerator-rosettanet/rnif-message-processing.md) </span></span>  
 [<span data-ttu-id="fd5a3-130">管理設定、 憑證、 資料庫和安全性</span><span class="sxs-lookup"><span data-stu-id="fd5a3-130">Manage configuration, certificates, databases, and security</span></span>](manage-configuration-certificates-databases-security.md)