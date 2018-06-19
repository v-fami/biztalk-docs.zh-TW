---
title: 支援可為 Null 的型別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a5ea191-09d5-47ab-a197-390fbbcf6306
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abd277db970a00e9d7d8f20de65e85c607c2a861
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278718"
---
# <a name="support-for-nullable-types"></a><span data-ttu-id="40974-102">可為 Null 型別的支援</span><span class="sxs-lookup"><span data-stu-id="40974-102">Support for Nullable Types</span></span>
<span data-ttu-id="40974-103">此規則引擎支援在商務規則中使用可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="40974-103">The rule engine supports using nullable types in a business rule.</span></span> <span data-ttu-id="40974-104">您可以在 .NET 類別繫結、XML 繫結和資料庫繫結中使用可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="40974-104">You can use nullable types in .NET class bindings, XML bindings, and database bindings.</span></span> <span data-ttu-id="40974-105">目前，商務規則編輯器工具不支援在商務規則中使用可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="40974-105">Currently, the Business Rule Composer tool does not support using nullable types in a business rule.</span></span> <span data-ttu-id="40974-106">當您以程式設計方式建立規則時，可以使用可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="40974-106">You can use the nullable types when creating rules programmatically.</span></span>  
  
## <a name="using-nullable-types-in-net-class-bindings"></a><span data-ttu-id="40974-107">在 .NET 類別繫結中使用可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="40974-107">Using Nullable Types in .NET Class Bindings</span></span>  
 <span data-ttu-id="40974-108">當屬性或欄位的型別是可為 Null 的型別時，您可以建立該屬性或欄位的類別成員繫結。</span><span class="sxs-lookup"><span data-stu-id="40974-108">You can create a class member binding to a property or a field whose type is a nullable type.</span></span> <span data-ttu-id="40974-109">當方法使用可為 Null 型別的參數及/或傳回可為 Null 型別的值時，您也可以建立該方法的類別成員繫結。</span><span class="sxs-lookup"><span data-stu-id="40974-109">You can also create a class member binding to a method that takes a parameter of nullable type and/or returns a value of nullable type.</span></span> <span data-ttu-id="40974-110">下列範例程式碼示範如何存取可為 Null 的欄位，以及如何從商務規則中的方法存取可為 Null 型別的傳回值。</span><span class="sxs-lookup"><span data-stu-id="40974-110">The following sample code demonstrates how to access a nullable field, and how to access a return value of nullable type from a method in a business rule.</span></span> <span data-ttu-id="40974-111">如果您執行主控台應用程式以下列程式碼，因為它是，您會看到的值**prop**欄位設定為 5。</span><span class="sxs-lookup"><span data-stu-id="40974-111">If you execute a console application with the following code as it is, you will see that the value of the **prop** field is set to 5.</span></span> <span data-ttu-id="40974-112">如果您未初始化**prop**類別中的欄位，或將它設為 null，執行程式碼，初始化，您會看到的值**prop**欄位設為 1。</span><span class="sxs-lookup"><span data-stu-id="40974-112">If you do not initialize the **prop** field in the class or initialize it to null and run the code, you will see that the value of the **prop** field is set to 1.</span></span>  
  
```  
using Microsoft.RuleEngine;  
namespace UseNullableAsm  
{  
    class Program  
    {  
        public class Class1  
        {  
            public int? prop = 1;  
            private int? prop2 = 4;  
            public int? GetProp2()  
            {  
                return prop2;  
            }  
        }  
  
        static void Main(string[] args)  
        {  
            //Create the class binding for the Class1 class  
            ClassBinding cbCls1 = new ClassBinding(typeof(Class1));  
  
            //Create the class member binding to the GetProp2 method of Cls1 class  
            ClassMemberBinding cmGetProp2 = new ClassMemberBinding("GetProp2", cbCls1);  
  
            //Create the class member binding to the to GET the value of prop  
            ClassMemberBinding cmGetProp = new ClassMemberBinding("prop", cbCls1);  
  
            //Create arguments for the prop1 field, which is prop1 + GetProp2()  
            UserFunction ufGetProp = new UserFunction(cmGetProp);  
            Add addArg = new Add(ufGetProp, new UserFunction(cmGetProp2));  
            ArgumentCollection al1 = new ArgumentCollection();  
            al1.Add(addArg);  
  
            //Set the value of prop to prop1 + cmGetPro2()  
            ClassMemberBinding cmProp = new ClassMemberBinding("prop", cbCls1, al1);  
  
            //Create a userfunction based on cmProp and add to the action collection  
            UserFunction ufProp = new UserFunction(cmProp);  
            ActionCollection ac = new ActionCollection();  
            ac.Add(ufProp);  
  
            //Create the condition list IF prop == 1  
            Equal eq = new Equal(ufGetProp, new Constant(1));  
  
            //Create the rule   
            // If (prop == 1)  
            // Then prop = prop + GetProp2()  
            Rule rl = new Rule("NullableTestRule", eq, ac);  
  
            //Create the condition list IF prop != 1  
            NotEqual neq = new NotEqual(ufGetProp, new Constant(1));  
  
            //Set the value of prop to prop to 1  
            Constant ct = new Constant(1);  
            ArgumentCollection al2 = new ArgumentCollection();  
            al2.Add(ct);  
  
            //Create class member binding to prop field with argument value 1  
            ClassMemberBinding cmSetProp = new ClassMemberBinding("prop", cbCls1, al2);  
  
            //Create a userfunction based on cmSetProp and add to the action collection  
            UserFunction ufSetProp = new UserFunction(cmSetProp);  
            ActionCollection ac2 = new ActionCollection();  
            ac2.Add(ufSetProp);  
  
            //Create the second rule   
            // If (prop != 1)  
            // Then prop = 1  
            Rule rl2 = new Rule("NullableTestRule2", neq, ac2);  
  
            //Create the policy and add both the rules to the policy  
            RuleSet rs = new RuleSet("NulableTestPolicy");  
            rs.Rules.Add(rl);  
            rs.Rules.Add(rl2);  
  
            //Create the .NET object fact  
            Class1 cls1Obj = new Class1();  
  
            //Print the value of the field prop before executing the policy  
            Console.WriteLine("Value of the prop field is " + cls1Obj.prop);  
  
            //Execute the policy  
            PolicyTester pt = new PolicyTester(rs);  
            pt.Execute(cls1Obj);  
  
            //Print the value of the field prop after executing the policy  
            Console.WriteLine("Value of the prop field is " + cls1Obj.prop);  
        }  
    }  
}  
```  
  
## <a name="using-nullable-types-in-database-bindings"></a><span data-ttu-id="40974-113">在資料庫繫結中使用可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="40974-113">Using Nullable Types in Database Bindings</span></span>  
 <span data-ttu-id="40974-114">您也可以在資料庫繫結中使用可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="40974-114">You can also use nullable types in database bindings.</span></span> <span data-ttu-id="40974-115">下列範例程式碼片段會示範如何在資料庫繫結中使用可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="40974-115">The following sample code fragment shows you how to use a nullable type in database bindings.</span></span>  
  
```  
DataColumnBinding dcBinding = new DataColumnBinding(“col”, typeof(int?), dbBinding);  
```  
  
 <span data-ttu-id="40974-116">假設您有一項規則的條件來檢查值的資料庫資料行等於 3。</span><span class="sxs-lookup"><span data-stu-id="40974-116">Suppose you have a rule with a condition that checks the value of a database column to see if equals 3.</span></span> <span data-ttu-id="40974-117">如果資料行的值為 null，運算式會評估為 false。</span><span class="sxs-lookup"><span data-stu-id="40974-117">If the value of the column is null, the expression evaluates to false.</span></span> <span data-ttu-id="40974-118">它不會造成例外狀況。</span><span class="sxs-lookup"><span data-stu-id="40974-118">It does not cause an exception.</span></span>  
  
## <a name="using-nullable-types-in-xml-bindings"></a><span data-ttu-id="40974-119">在 XML 繫結中使用可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="40974-119">Using Nullable Types in XML Bindings</span></span>  
 <span data-ttu-id="40974-120">同樣地，您也可以在 XML 繫結中使用可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="40974-120">Similarly, you can use nullable types in XML bindings.</span></span> <span data-ttu-id="40974-121">下列範例程式碼片段示範如何在 XML 繫結中使用可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="40974-121">The following sample code fragment shows how to use a nullable type in XML bindings.</span></span>  
  
```  
XMLDocumentFieldBinding xfb1 = new XMLDocumentFieldBinding(typeof(int?),"ID",xdb);  
```