---
title: "維護不可否認性資料庫資料表 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- databases, purging
- databases, non-repudiation database
- maintaining databases, purging
- purging databases
- databases, maintaining
- non-repudiation, database
ms.assetid: 29222510-325b-4cd7-854b-6f548a63fd08
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 182172eccddcaad684f35335708dce6027fb111f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="maintaining-the-non-repudiation-database-tables"></a>維護不可否認性資料庫資料表
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]存放在 BTARNArchive 資料庫的 MessageStorageIn 和 MessageStorageOut 資料表中的不可否認性目的的訊息。 這些資料表中的許多訊息可能會影響系統效能。 如有必要，您可能需要定期清除和封存這些資料表中的訊息，以維護這些不可否認性資料庫資料表。  
  
## <a name="routine-database-maintenance"></a>資料庫日常維護  
 當[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]收到訊息時，它一律會將訊息儲存在 MessageStorageIn 資料表，並設定初始**ToBePurged**欄位設為"1"，這表示訊息不需要不可否認性。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]然後解密，並將解碼的訊息，以判斷協議為何。 解密與解碼之後，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會檢視協議，決定是否必須以不可否認性目的來儲存訊息。 因此，它會設定如果**ToBePurged**欄位設為"0"，並填入訊息的其他欄位。 如果沒有，它會維持**ToBePurged**欄位為"1"並不填入訊息的其他欄位。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]不會自動刪除訊息**ToBePurged**欄位設定為"1"。 此外，它也不會將以不可否認性目的儲存的訊息封存至其他資料表。 這兩類訊息會在 MessageStorageIn 資料表中逐漸累積，進而影響效能。 在資料庫的例行性維護工作中，您可能需要執行下列動作：  
  
-   執行預存程序包含下列 SQL 陳述式來刪除所有訊息於 MessageStorageIn 資料表其**ToBePurged**欄位是否不等於"0":  
  
    ```  
    delete MessageStorageIn where ToBePurged <> 0  
    ```  
  
-   在經過一段適當的時間 (由公司原則所決定) 之後，執行預存程序，以便將不可否認性的訊息封存至不會影響效能的離線資料庫。 您可以使用，以判斷這段期間**TimeCreated** MessageStorageIn 資料表中的欄位。 訊息的不可否認性期限到期之後，您可以從封存資料庫刪除訊息，使用下列 SQL 陳述式 （這會刪除超過七日的訊息）：  
  
    ```  
    delete <archive table name> where datediff(d, TimeCreated, GetUTCDATA())>7  
    ```  
  
> [!NOTE]
>  **TimeCreated** MessageStorageIn 資料表中的欄位是使用 utc 格式。  
  
> [!NOTE]
>  您不應該刪除過去一小時之內收到的內送訊息。  
  
 當 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 傳送外寄訊息時，會先存取不可否認性協議。 如果協議要求不可否認性，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 就會將訊息儲存在 MessageStorageOut 資料表中。 如果沒有此要求，則不會將訊息儲存在資料表內。 這表示沒有不需要**ToBePurged**本表中的欄位。 MessageStorageOut 資料表需要的唯一維護動作，便是在經過一段適當的時間後，將不可否認性訊息封存至離線資料庫，並在超過不可否認性時段後刪除每個訊息。 若要如此，可利用下列 SQL 陳述式 (刪除超過七日的訊息)：  
  
```  
delete MessageStorageOut where datediff(d, TimeCreated, GetUTCDATA())>7  
```  
  
## <a name="see-also"></a>另請參閱  
 [RNIF 訊息處理](../../adapters-and-accelerators/accelerator-rosettanet/rnif-message-processing.md)   
 [管理設定、 憑證、 資料庫和安全性](manage-configuration-certificates-databases-security.md)