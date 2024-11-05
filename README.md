maps = { 'A' : set (['B','H']),
         'B' : set (['A','C','H']),
         'C' : set (['B','D','E']),
         'D' : set (['C','E','F','G','H']),
         'E' : set (['C','D']),
         'F' : set (['D','G']),
         'G' : set (['H','D','F']),
         'H' : set (['A','B','D','G'])
         }

def short_traversals(maps, start, goal):
  explore = []
  queue = [[start]]

  if start == goal :
    return "start is the goal"

  while queue:
    path = queue.pop(0)
    node = path[-1]

    if node not in explore :
      neighbours = maps[node]

      for neighbour in neighbours :
        new_path = list(path)
        new_path.append(neighbour)
        queue.append(new_path)

        if neighbour == goal:
          return new_path

      explore.append(node)


  return "sory, node that your choses there is no"


start = input("masukkan kota awal : ")
goal = input("masukkan kota tujuan : ")

print(short_traversals(maps, start, goal))
