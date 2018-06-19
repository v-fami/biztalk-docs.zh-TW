---
title: 支援安全通訊端層 (SSL) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSL
ms.assetid: 012a5be0-bab8-4a60-9d63-b9684b91e4a7
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 086ec1715d76a25649cb2285b31b3df790b0fe3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214158"
---
# <a name="supporting-secure-sockets-layer-ssl"></a>支援安全通訊端層 (SSL)
若要實作安全通訊端層 (SSL) 通訊協定的用戶端電腦與 MRSR 伺服器之間部署中，您需要要求您的網際網路資訊服務 (IIS) 伺服器上設定 「 伺服器驗證 」 憑證。  
  
 一個憑證應該用於網路負載平衡 (NLB) 叢集中的所有伺服器。 您應該確定在憑證要求中所使用的名稱是虛擬的主機名稱，而不是個別的伺服器名稱。