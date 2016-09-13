

    def match_ends(words):
        res=sum(1 for i in words if len(i)>1 and i[0]==i[len(i)-1])
        return res
    def front_x(words):
        listx=list()
        listother=list()
        for i in words:
            if i[0]=="x":
                listx.append(i)
                continue
            else:
                listother.append(i)
                continue
        listx.sort()
        listother.sort()
        listx.extend(listother)
        return listx  
    def sort_last(tuples):
        lastE=list()
        res=list()
        for i in tuples:
            lastE.append(i[len(i)-1])
        indexSort=sorted(range(len(lastE)), key=lambda k: lastE[k])
        for i in indexSort:
            res.append(tuples[i])
        return res
    def remove_adjacent(nums):
        if len(nums)<2:
            return nums
        res=list()
        res.append(nums[0])
        for i in nums[1:]:
            if not i==res[-1]:
                res.append(i)
                continue
        return 
    def linear_merge(list1, list2):
        res=list()
        i1=0
        max1=len(list1)
        i2=0
        max2=len(list2)
        for i in range(0,max1+max2-1):
            if i1>(max1-1):
                res.extend(list2[i2:(max2-1)])
                break
            if i2>(max2-1):
                res.extend(list1[i1:(max1-1)])
                break
            if list1[i1]<=list2[i2]:
                res.append(list1[i1])
                i1=i1+1
                continue
            if list1[i1]>list2[i2]:
                res.append(list2[i2])
                i2=i2+1
                continue
        return res
    def test(got, expected):
        prefix = 'OK' if got == expected else ' X'
        # !r prints a Python representation of the strings (complete with quotes)
        print ' {} got: {!r} expected: {!r}'.format(prefix, got, expected)


    def main1():
        print 'match_ends'
        test(match_ends(['aba', 'xyz', 'aa', 'x', 'bbb']), 3)
        test(match_ends(['', 'x', 'xy', 'xyx', 'xx']), 2)
        test(match_ends(['aaa', 'be', 'abc', 'hello']), 1)
    
        print
        print 'front_x'
        test(front_x(['bbb', 'ccc', 'axx', 'xzz', 'xaa']),
            ['xaa', 'xzz', 'axx', 'bbb', 'ccc'])
        test(front_x(['ccc', 'bbb', 'aaa', 'xcc', 'xaa']),
            ['xaa', 'xcc', 'aaa', 'bbb', 'ccc'])
        test(front_x(['mix', 'xyz', 'apple', 'xanadu', 'aardvark']),
            ['xanadu', 'xyz', 'aardvark', 'apple', 'mix'])
        
        print
        print 'sort_last'
        test(sort_last([(1, 3), (3, 2), (2, 1)]),
             [(2, 1), (3, 2), (1, 3)])
        test(sort_last([(2, 3), (1, 2), (3, 1)]),
             [(3, 1), (1, 2), (2, 3)])
        test(sort_last([(1, 7), (1, 3), (3, 4, 5), (2, 2)]),
             [(2, 2), (1, 3), (3, 4, 5), (1, 7)])
    def main2():
        print 'remove_adjacent'
        test(remove_adjacent([1, 2, 2, 3]), [1, 2, 3])
        test(remove_adjacent([2, 2, 3, 3, 3]), [2, 3])
        test(remove_adjacent([]), [])
    
        print
        print 'linear_merge'
        test(linear_merge(['aa', 'xx', 'zz'], ['bb', 'cc']),
            ['aa', 'bb', 'cc', 'xx', 'zz'])
        test(linear_merge(['aa', 'xx'], ['bb', 'cc', 'zz']),
            ['aa', 'bb', 'cc', 'xx', 'zz'])
        test(linear_merge(['aa', 'aa'], ['aa', 'bb', 'bb']),
            ['aa', 'aa', 'aa', 'bb', 'bb'])


    main1()
    main2()

    match_ends
     OK got: 3 expected: 3
     OK got: 2 expected: 2
     OK got: 1 expected: 1
    
    front_x
    ['xaa', 'xzz']
    ['axx', 'bbb', 'ccc']
     OK got: ['xaa', 'xzz', 'axx', 'bbb', 'ccc'] expected: ['xaa', 'xzz', 'axx', 'bbb', 'ccc']
    ['xaa', 'xcc']
    ['aaa', 'bbb', 'ccc']
     OK got: ['xaa', 'xcc', 'aaa', 'bbb', 'ccc'] expected: ['xaa', 'xcc', 'aaa', 'bbb', 'ccc']
    ['xanadu', 'xyz']
    ['aardvark', 'apple', 'mix']
     OK got: ['xanadu', 'xyz', 'aardvark', 'apple', 'mix'] expected: ['xanadu', 'xyz', 'aardvark', 'apple', 'mix']
    
    sort_last
     OK got: [(2, 1), (3, 2), (1, 3)] expected: [(2, 1), (3, 2), (1, 3)]
     OK got: [(3, 1), (1, 2), (2, 3)] expected: [(3, 1), (1, 2), (2, 3)]
     OK got: [(2, 2), (1, 3), (3, 4, 5), (1, 7)] expected: [(2, 2), (1, 3), (3, 4, 5), (1, 7)]
    remove_adjacent
     OK got: [1, 2, 3] expected: [1, 2, 3]
     OK got: [2, 3] expected: [2, 3]
     OK got: [] expected: []
    
    linear_merge
      X got: ['aa', 'bb', 'cc', 'xx'] expected: ['aa', 'bb', 'cc', 'xx', 'zz']
      X got: ['aa', 'bb', 'cc', 'xx'] expected: ['aa', 'bb', 'cc', 'xx', 'zz']
      X got: ['aa', 'aa', 'aa', 'bb'] expected: ['aa', 'aa', 'aa', 'bb', 'bb']



    def donuts(count):
        res="Number of donuts: "
        if count<10:
            res2=count
        else:
            res2="many"
        resF=res+str(res2)
        return resF
    def both_ends(s):
        res=""
        if len(s)<2:
            return ""
        s1=s[0:2]
        s2=s[(len(s)-2):(len(s))]
        return s1+s2
    def fix_start(s):
        s1=s[0]
        s2=s[1:len(s)]
        return s1+s2.replace(s1,"*")
    def mix_up(a,b):
        a1=a[0:2]
        a2=a[2:len(a)]
        b1=b[0:2]
        b2=b[2:len(b)]
        aa=b1+a2
        bb=a1+b2
        return aa+" "+bb
    def verbing(s):
        if len(s)<3:
            return s
        if s[(len(s)-3):(len(s))]=="ing":
            return s+"ly"
        return s+"ing"
    def not_bad(s):
        i1=s.find("not")
        i2=s.find("bad")
        if i2>i1:
            if i1==0:
                return "good"+s[(i2+3):len(s)]
            return s[0:i1]+"good"+s[(i2+3):len(s)]
        return s
    def front_back(a,b):
        lena=len(a)
        lenb=len(b)
        if lena%2==0:
            fronta=a[0:((lena/2))]
            backa=a[(lena/2):lena]
        else:
            n=(lena-1)/2
            fronta=a[0:(n+1)]
            backa=a[(n+1):lena]
        if lenb%2==0:
            frontb=b[0:((lenb/2))]
            backb=b[(lenb/2):lenb]
        else:
            n=(lenb-1)/2
            frontb=b[0:(n+1)]
            backb=b[(n+1):lenb]
        return fronta+frontb+backa+backb


    def main3():
        print 'donuts'
        # Each line calls donuts, compares its result to the expected for that call.
        test(donuts(4), 'Number of donuts: 4')
        test(donuts(9), 'Number of donuts: 9')
        test(donuts(10), 'Number of donuts: many')
        test(donuts(99), 'Number of donuts: many')
    
        print
        print 'both_ends'
        test(both_ends('spring'), 'spng')
        test(both_ends('Hello'), 'Helo')
        test(both_ends('a'), '')
        test(both_ends('xyz'), 'xyyz')
    
      
        print
        print 'fix_start'
        test(fix_start('babble'), 'ba**le')
        test(fix_start('aardvark'), 'a*rdv*rk')
        test(fix_start('google'), 'goo*le')
        test(fix_start('donut'), 'donut')
    
        print
        print 'mix_up'
        test(mix_up('mix', 'pod'), 'pox mid')
        test(mix_up('dog', 'dinner'), 'dig donner')
        test(mix_up('gnash', 'sport'), 'spash gnort')
        test(mix_up('pezzy', 'firm'), 'fizzy perm')
    def main4():
        print 'verbing'
        test(verbing('hail'), 'hailing')
        test(verbing('swiming'), 'swimingly')
        test(verbing('do'), 'do')
        
        print
        print 'not_bad'
        test(not_bad('This movie is not so bad'), 'This movie is good')
        test(not_bad('This dinner is not that bad!'), 'This dinner is good!')
        test(not_bad('This tea is not hot'), 'This tea is not hot')
        test(not_bad("It's bad yet not"), "It's bad yet not")
    
        print
        print 'front_back'
        test(front_back('abcd', 'xy'), 'abxcdy')
        test(front_back('abcde', 'xyz'), 'abcxydez')
        test(front_back('Kitten', 'Donut'), 'KitDontenut')


    main3()
    main4()

    donuts
     OK got: 'Number of donuts: 4' expected: 'Number of donuts: 4'
     OK got: 'Number of donuts: 9' expected: 'Number of donuts: 9'
     OK got: 'Number of donuts: many' expected: 'Number of donuts: many'
     OK got: 'Number of donuts: many' expected: 'Number of donuts: many'
    
    both_ends
     OK got: 'spng' expected: 'spng'
     OK got: 'Helo' expected: 'Helo'
     OK got: '' expected: ''
     OK got: 'xyyz' expected: 'xyyz'
    
    fix_start
     OK got: 'ba**le' expected: 'ba**le'
     OK got: 'a*rdv*rk' expected: 'a*rdv*rk'
     OK got: 'goo*le' expected: 'goo*le'
     OK got: 'donut' expected: 'donut'
    
    mix_up
     OK got: 'pox mid' expected: 'pox mid'
     OK got: 'dig donner' expected: 'dig donner'
     OK got: 'spash gnort' expected: 'spash gnort'
     OK got: 'fizzy perm' expected: 'fizzy perm'
    verbing
     OK got: 'hailing' expected: 'hailing'
     OK got: 'swimingly' expected: 'swimingly'
     OK got: 'do' expected: 'do'
    
    not_bad
     OK got: 'This movie is good' expected: 'This movie is good'
     OK got: 'This dinner is good!' expected: 'This dinner is good!'
     OK got: 'This tea is not hot' expected: 'This tea is not hot'
     OK got: "It's bad yet not" expected: "It's bad yet not"
    
    front_back
     OK got: 'abxcdy' expected: 'abxcdy'
     OK got: 'abcxydez' expected: 'abcxydez'
     OK got: 'KitDontenut' expected: 'KitDontenut'



    




    1




    


    
