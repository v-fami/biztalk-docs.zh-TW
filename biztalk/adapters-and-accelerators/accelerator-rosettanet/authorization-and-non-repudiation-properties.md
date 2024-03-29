---
title: 授權與不可否認性屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- authorization properties
- non-repudiation, properties
ms.assetid: e752b95b-9dae-4403-8f3e-3a0a50acd519
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d7088b25ec2526c19c60d21c9929afb92be42a7
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752758"
---
# <a name="authorization-and-non-repudiation-properties"></a>授權與不可否認性屬性
本主題說明交易夥伴介面程序 (PIP) 的 `Is Authorization Required`、`Non-Repudiation of Origin and Content` 和 `Non-Repudiation Required (Acknowledgement of Receipt)` 屬性的行為。 它也會說明這些屬性的組合，Microsoft[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]支援。  

 您可以設定這些屬性上**活動**的程序組態設定 區段中的程序組態屬性 索引標籤[!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)]管理主控台。 如需詳細資訊，請參閱 <<c0> [ 如何建立或編輯流程組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。  

## <a name="property-behavior"></a>屬性行為  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 根據 `Is Authorization Required`、`Non-Repudiation of Origin and Content` 和 `Non-Repudiation Required (Acknowledgement of Receipt)` 屬性的設定表現下列行為。  


|                        屬性                         |                                                                                                                                                                             屬性值為 True 時的行為                                                                                                                                                                             |                                                                               屬性值為 False 時的行為                                                                               |
|---------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               `Is Authorization Required`               | 必須簽署內送動作或信號訊息;否則，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]會拒絕該訊息。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 若個人/角色未經授權執行活動，不接受商務文件。 | 不需要對內送動作或信號訊息進行簽署， 但仍可使用訊息 RNIF 標頭部分中的交易夥伴 DUNS 編號進行簡單的授權。 |
|         `Non-Repudiation of Origin and Content`         |                                                                                                簽署外寄動作或信號訊息。 動作訊息將以原始接收格式，存放在 BTARNDATA 資料庫中的 MessageStorageOut 資料表。                                                                                                 |                                                             不存放外寄動作或信號訊息。                                                              |
| `Non-Repudiation Required (Acknowledgement of Receipt)` |                                                                                 必須簽署內送動作或信號訊息。 內送訊息將存放在 BTARNDATA 資料庫的 MessageStorageIn 表格中。 通知中必須含有訊息摘要。                                                                                  |                                                             不存放內送動作或信號訊息。                                                              |

## <a name="property-support"></a>支援的屬性  
 下表顯示 `Is Authorization Required`、`Non-Repudiation of Origin and Content` 和 `Non-Repudiation Required (Acknowledgement of Receipt)` 屬性組合的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 支援。  

> [!IMPORTANT]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 必須是登入同時動作訊息與信號訊息，或不動作訊息也不單一訊息。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 執行不支援簽署動作，但不是簽署信號，反之亦然。  
> 
> [!IMPORTANT]
>  若 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 對輸出訊息加上簽章，就必須將此訊息儲存在 BTARNARCHIVE 資料庫的 MessageStorageOut 資料表內。  

|需要授權|來源與內容的不可否認性|接收通知 - 需要不可否認性|BTARN 是否支援？|  
|-------------------------------|--------------------------------------------|--------------------------------------------------------------|-------------------------|  
|`False`|`False`|`False`|是|  
|`False`|`False`|`True`|否\*|  
|`False`|`True`|`False`|否\*\*|  
|`False`|`True`|`True`|否\*\*\*|  
|`True`|`False`|`False`|[是]\*\*\*\*|  
|`True`|`False`|`True`|[是]\*\*\*\*|  
|`True`|`True`|`False`|是|  
|`True`|`True`|`True`|是|  

 \* [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 不支援此組合，因為您必須簽署信號，並不簽署動作。  

 \*\* [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 不支援此組合，因為它需要簽署動作，而且不簽署信號。  

 \*\*\* [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 不支援此組合，因為設為不可否認`True`的動作與信號表示[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]執行授權。 因此，此組合無效。  

 \*\*\*\* 當您設定`Is Authorization Required`來`True`並`Non-Repudiation of Origin and Content`來`False`，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]會將訊息儲存在不可否認性資料表中。  

## <a name="see-also"></a>另請參閱  
 [如何建立或編輯程序設定](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)